## Practice 1｜Drum Kit
> 開始於[time=Thu, Oct 17, 2024 1:11 PM]

### 主題
透過 JS 使鍵盤按下後播放出對應按鍵的聲音，並同時產生一個特效，
在按下其他鍵後會關閉該特效並於新按鍵中啟用。

## Practice 2｜Clock
> 開始於[time=Fri, Oct 18, 2024 1:49 PM]
http://127.0.0.1:5500/02_clock/index.html
### 主題
用JS與CSS搭配製作一個實時的時鐘效果
### Step1 製作時針、分針、秒針
利用 class `hand` 樣式來製作
### Step2 設定定時器邏輯
1. 先建立一個每秒執行的函數
```javascript=
//建立一個函數、每秒都執行
function setDate(){
    console.log("HI");
}
//每一秒執行 setDate 這個函數
setInterval(setDate, 1000);
```
2. 獲取秒數

```javascript=
//定義了一個 setDate 的函數。
function setDate(){
    const now = new Date();//創建一個新的日期對象，代表當前時間
    const seconds = now.getSeconds();//從 now 日期對象中獲取秒數（0 到 59）
    console.log(seconds);//將秒數輸出到控制台
    }
```

3. 將獲取的秒數轉為 rotate 的角度，讓秒針會根據當前時間動態旋轉

```javascript=
// 選擇器選取 .second-hand 的 DOM 元素
const secondHand = document.querySelector('.second-hand');

// 定義一個函數來設定時間
function setDate(){
    // 創建一個新的日期對象，代表當前時間
    const now = new Date();
    
    // 從 now 日期對象中獲取秒數（0 到 59）
    const seconds = now.getSeconds();
    
    // 計算秒針應該旋轉的角度
    // 每分鐘有 360 度，60 秒鐘內需要旋轉 360 度
    // 加上 90 度是因為指針預設是 45 分
    const secondsDegrees = ((seconds / 60) * 360)+90;
    
    // 使用 CSS 的 transform 屬性和 rotate() 函數來旋轉秒針
    secondHand.style.transform = `rotate(${secondsDegrees}deg)`;
    
    // 將秒數輸出到控制台
    console.log(seconds);
}
```


### Step3 利用當前時間來取得對應角度


### JS 備註
**1. setDate()**
`setDate()` 括號裡面填入幾號

**2. setInterval()**
```
setInterval(displayHello, 1000);
```
常用於：
1. 定期更新 UI 或 DOM 元素
2. 執行長期運行的背景任務
3. 創建動畫或交互式效果

**3. `rotate(${secondsDegrees}deg)`;**

1.rotate()中加入表達式${secondsDegrees}計算出秒針應該旋轉的角度
2.deg:表示角度單位，確保輸入值被正確解釋為角度
3.根據 MDN 文件，rotate() 函數接受以下單位：
deg（度）
grad（弧度）
rad（弧度）
turn（轉）


### CSS 備註
**transform-origin**
變形的軸心，預設為物件的中心點，
在這個範例中，設定為100%(right)可以使其從時鐘面的中心點開始旋轉。

**transform:rotate()**
旋轉物件，數值後方要加上角度deg，
可超過360度，正值為順時針轉，負值為逆時針旋轉。

**transition-timing-function: cubic-bezier()**
設定動畫轉場所依據的貝茲曲線，可以透過chrome的開發者工具來進行可視化調整。


