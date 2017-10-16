## 五子棋

### UI部分
使用canvas绘制棋盘、棋子
#### 棋盘绘制
```
//绘制背景色
    fillRect(0, 0, 500, 560);
//棋盘线条
    for (let i = 0; i < 15; i++) {
       this.con.moveTo(0, i * 30);
       this.con.lineTo(420, i * 30);
    }
    for (let i = 0; i < 15; i++) {
       this.con.moveTo(i * 30, 0);
       this.con.lineTo(i * 30, 420);
    }
//棋子，计算出点击位置的x，y坐标，并以此为中心绘制圆
    arc(x * 30, y * 30, 14, 0, 2 * Math.PI, false);

```
#### JS部分

### 棋盘点击事件
    计算点击位置与canvas的距离，计算出点击位置在棋盘上的坐标位置
### 胜负逻辑判定
将白棋、黑棋所下的五子棋的位置按照如图所示的坐标系分别保存在一个二维数组里，那
么只有四种情况下胜利的，
1. 横着一排连续五个胜利，也就是x一样，y连续加1
```
arr是已经按照横排排序好的棋子数组
function (arr) {
            arr = this._acrossSort(arr);
            //横排胜利
            for (let i = 0, j = 0; i < arr.length - 1; i++) {
                if (arr[i][1] === arr[i + 1][1] && arr[i][0] + 1 === arr[i + 1][0]) {
                    j++;
                    if (j === 4) {
                        return true
                    }
                }
                else {
                    j = 0;
                }
            }
            return false
        }
```
2. 竖着一排连续五个胜利，也就是y一样，x连续加1
3. 斜着一排连续五个胜利，也就是x+y的值都一样并x，y的值都连续加一
4. 反着斜排连续五个胜利，把坐标以（7，0）为轴改变坐标点的值，然后同上

 