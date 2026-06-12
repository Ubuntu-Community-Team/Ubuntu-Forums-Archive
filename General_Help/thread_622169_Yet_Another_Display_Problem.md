---
title: "Yet Another Display Problem"
date: 2007-11-24
forum: General Help
---

### Post by trirnoth on 2007-11-24
I hopefully read just about all I can on this and didn't miss an obvious answer...

Just picked up a Samsung 245BW and have been having problems using this to it's fullest 1920x1200 resolution.

cvt 1920 1200 60
# 1920x1200 59.88 Hz (CVT 2.30MA) hsync: 74.56 kHz; pclk: 193.25 MHz
Modeline "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync

The above gives an error of
WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200

The manual located at (PDF Alert!) [http://downloadcenter.samsung.com/content/UM/200711/20071115165716234_BN59-00565F-04Eng.pdf](http://downloadcenter.samsung.com/content/UM/200711/20071115165716234_BN59-00565F-04Eng.pdf) shows 
HorizSync		30.0-81.0
VertRefresh	56.0-75.0
Pixel Clock	154.0

Setting the modline to 154 manually will display using 1920x1200, but with static at 50 Hz versus 60 Hz no matter what I do to force 60.

Additional probable useless information:
Running 7.10 w/ 2.6..22-14
Nvidia Driver 100.14.19

I can provide my xorg.conf file if needed, though it is pretty standard after running sudo dpkg-reconfigure -phigh xserver-xorg.

Thnx for making it this far.

---

### Post by trirnoth on 2007-11-25
Anyone looking for an answer to this... I found it.
Apparently my FX5200 Ultra is not enough to pipe 1920x1200 through DVI.
Works beautifully with VGA.

I was not thinking hardware at all when I started this posting until I ran across [http://oclug.on.ca/archives/oclug/2007-October.txt](http://oclug.on.ca/archives/oclug/2007-October.txt) where the questioner states ¨I didn't have any problems with desktop size when I had  the monitor hooked up via the VGA connection.¨

---

