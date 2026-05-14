# 20260514

gap.txt 和 state.txt 用于更新判据，更改文本文件后点击更新判据，就可以直接应用TXT中最新的判据，注意txt中采用英文的等号

<img width="1258" height="622" alt="e86cc864f08f4d0e7f7c035b7e8a037e" src="https://github.com/user-attachments/assets/e0f26e30-9f19-465b-9e51-44a23875b802" />

<img width="300" height="572" alt="image" src="https://github.com/user-attachments/assets/f088b3e0-4234-4549-9a66-0a5388bed07c" />

<img width="436" height="224" alt="image" src="https://github.com/user-attachments/assets/f5ffcc4d-6f6a-45fb-adb7-aa5abacfd0ea" />


# 1 状态判据
## 1.1 能量判据
S4-S11幅度加和，小于阈值1（5000）输出标记0，大于阈值2（40000）输出标记1，其他输出标记2，第一个标记0，1，2
## 1.2 方向判据1
S4-S11纯z方向判断，传感器X和Y值的平方小于1000时（平面圆内），认为矢量是Z方向的，置为1否则为0，8个传感器生成一个序列，加和小于阈值（4）时，认为满足Z向判据。输出第二个标记0或1。
## 1.3 方向判据2
传感器XY赋值确定象限1234，8个传感器生成一个序列，序列两两相减（序列1减序列2，3-4...），得到的差值取绝对值后模2，当1个keeper的2个传感器象限做轴对称时得到1，若做原点对称时得到0。加和得到第三个标记0，1，2，3，4。
## 1.4 状态判断
```python
依据三个标记
“101” ＝ “过度状态，吸力加强但仍不足”
“002” ＝ “无吸力接触”
“001” ＝ “无吸力接触”
“003”  ＝ “接触卸磁微弱吸力”
“204” ＝ “接触卸磁仍有吸力”
“004” ＝ “接触卸磁仍有较强吸力”
“110” ＝ “接触可靠磁吸附或非接触磁吸附”
“100” ＝ “有吸力”
“200” ＝ “非接触无吸力”
“201” ＝ “过度状态，吸力偏弱 或 非接触无吸力”
“211” ＝ “非接触磁吸附”
“202” ＝ “GAP”
“203” ＝ “GAP”
```

# 2 GAP判据
S4-S11的幅度减去S4-S11的均值，
差值绝对值的和若大于阈值（3000），则判定产生GAP
差值看符号，大于0为1，小于0为0，得到一个序列。
其中：
```python
“00001111”＝ “下部有GAP”
“11110000”＝ “上部有GAP”
“00111100”＝ “右部有GAP”
“11000011”＝ “左部有GAP”
“00111111”＝ “仅左上角接触”
“11110011”＝ “仅右下角接触”
“11000111”＝ “仅右上角接触”
```

# 实验依据
<img width="2712" height="1614" alt="20ac5b1871901611018bd8d22c8ef04e" src="https://github.com/user-attachments/assets/aeffe9fa-a0b7-4ce8-a65d-7f0179d4135a" />



# seefootsensordata
user E-language to make a app to see the sensor data

<img width="938" height="755" alt="image" src="https://github.com/user-attachments/assets/d781b823-6380-4627-bbde-cd73cd88ab68" />

<img width="951" height="755" alt="image" src="https://github.com/user-attachments/assets/355e6a55-9358-45b1-87f9-edd1e56d6f07" />

<img width="1398" height="1356" alt="image" src="https://github.com/user-attachments/assets/98637961-c7c9-487a-8b83-3954465a63ad" />


<img width="2062" height="1214" alt="image" src="https://github.com/user-attachments/assets/4e7d340b-fdc6-4128-aa9e-0661f01a971c" />

一个完整数据帧，13*3霍尔数据，接触开关数据*4，IMU数据*3
[14:40:37.855]接收←-1.262,-29.449,-3.829,3.839,-19.248,7.331,-2.127,-15.398,13.763,6.844,-20.959,-2.162,6.416,-16.727,9.919,1.711,-18.872,7.784,9.784,-39.670,8.194,4.692,-28.580,15.956,1.283,-12.009,5.203,-5.119,-24.877,8.216,12.404,-16.298,13.838,4.277,-22.670,16.000,14.889,-25.594,14.231,1,1,1,1,-1.166,-2.725,0.000
<img width="1570" height="882" alt="7f31f7ba946011ad5c510e6a78f51b88" src="https://github.com/user-attachments/assets/4e3288cd-42e5-412c-bdf7-08cd4d01f736" />

<img width="2439" height="1422" alt="6dc63e9426c160766a6058adfdf6dfd1" src="https://github.com/user-attachments/assets/0182508e-58d9-432d-becb-288a0b2615a4" />

<img width="2460" height="1395" alt="image" src="https://github.com/user-attachments/assets/fecd2956-7538-48a5-b1a7-8588106c5146" />
