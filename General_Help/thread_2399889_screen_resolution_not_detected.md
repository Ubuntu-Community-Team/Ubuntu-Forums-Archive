---
title: "screen resolution not detected"
date: 2018-08-30
forum: General Help
---

### Post by jfca283 on 2018-08-30
Hi, 
I'am using ubuntu 18.04 and I can't set the maximum screen resolution as my monitor suppots.
This is what I get from xrand -q
```
juan@juan-OptiPlex-7010:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 16384 x 16384
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected primary 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00  
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  

```

I am connecting my screen using a DVI/VGA adapter. 
I've recently added some modes specifying the 1920x1080 resolution. I ran the cvt line:
```
juan@juan-OptiPlex-7010:~$ cvt 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

```

What do I need to do in order to set my monitor with a higher resolution?
Thanks for your time and interest.

---

### Post by Autodave on 2018-08-31
What video card are you using and did you install a driver for it? If so, what driver and where did you get it from?

---

### Post by NM5TF on 2018-08-31
please post the output of

```
inxi -G
```

this will tell us your video card & drivers in use

tommy

---

### Post by jfca283 on 2018-09-01
```
juan@juan-OptiPlex-7010:~$ inxi -G
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Turks PRO [Radeon HD 7570]
           Display Server: x11 (X.Org 1.19.6 ) driver: radeon
           Resolution: 1024x768@60.00hz
           OpenGL: renderer: AMD TURKS (DRM 2.50.0 / 4.15.0-33-generic, LLVM 7.0.0)
           version: 3.3 Mesa 18.3.0-devel

```

---

### Post by NM5TF on 2018-09-02
have you tried to use xrandr to add the new mode ???

you already have the new information from cvt...run these commands in sequence...

```
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode DVI-0 "1920x1080_60.00"
```

this should add the new mode & apply it...your monitor should flash & then go to new resolution....

if not, then try this 
```
xrandr --output DVI-0 --mode "1920x1080_60.00"
```

good luck

tommy

---

### Post by jfca283 on 2018-09-02
Thanks,  NM5TF.
Your first recommendation worked flawless.

---

### Post by NM5TF on 2018-09-02
most XCLNT Juan---Buen Jale !!!

now if you could mark the thread SOLVED by using thread tools at top of your post #1 so others can see it

tommy

---

