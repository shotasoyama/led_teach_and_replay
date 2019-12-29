ロボットシステム学　課題1

# led_teach_and_replay

授業内ででたプログラムを改良し、LEDの光る順番を教示し
その順番を再現するプログラムを作成した。

[デモ動画](https://www.youtube.com)

## 動作環境

* ubuntu 18.04
* Raspberry Pi 3 Model B+
 * 接続ピン - GPIO16,20,21,GND
* LED 3つ 
* 抵抗 - 330[Ω]

## 準備

``` 
$ git clone https://github.com/shotasoyama/led_teach_and_replay.git
$ make
$ sudo insmod myled.ko
$ sudo chmod 666 /dev/myled0
```

## 操作方法

### 教示

``` 
$ echo 0 > /dev/myled0  
$ echo 1 > /dev/myled0  
$ echo 2 > /dev/myled0  
$ echo 3 > /dev/myled0  
```

上記の4行から光らせたいLEDの番号を任意の順番で光らせます。
（デモ動画は1→2→3→2→3）

### リプレイ

以下を実行すると教示した動きが再現されます。

``` 
$ echo R > /dev/myled0  
```

### 終了

``` 
$ echo 0 > /dev/myled0  
$ sudo rmmod myled.ko
```
