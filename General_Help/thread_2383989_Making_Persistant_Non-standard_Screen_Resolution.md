---
title: "Making Persistant Non-standard Screen Resolution"
date: 2018-02-01
forum: General Help
---

### Post by rbscairns on 2018-02-01
I am using Lubuntu 16.04. I needed to change my screen resolution to a non-standard 1280x720 so that circles look like circles and not ovals. I achieved this by entering in terminal
```
cvt 1280 720
```
This returned
```
# 1280x720 59.86 Hz (CVT 0.92M9) hsync: 44.77 kHz; pclk: 74.50 MHz
Modeline "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
```
I then entered
```
xrandr --newmode "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
```
and
```
xrandr --addmode VGA1 "1280x720_60.00"
```
This gave me the 1280x720 resolution option in Display Settings that I wanted.

The problem is that this option is not persistent. Each time I boot into Lubuntu, I have to re-enter the above in terminal to get my desired 1280x720 screen resolution option back.

[LIST=1]
[*]How can I make the 1280x720 screen resolution option permanent in Display Setting?
[*]How can I make the 1280x720 screen resolution default whenever I boot into Lubuntu?
[*]
[/LIST]
All help will be gratefully received and faithfully applied.

---

### Post by cruzer001 on 2018-02-01
Here's a quick fix

[https://askubuntu.com/questions/754231/how-do-i-save-my-new-resolution-setting-with-xrandr](https://askubuntu.com/questions/754231/how-do-i-save-my-new-resolution-setting-with-xrandr)

---

### Post by rbscairns on 2018-02-01
Thank you Cruser. Your advice worked like a charm.

I am now a VERY happy Ubuntu user!

---

### Post by cruzer001 on 2018-02-02
Welcome :)

---

