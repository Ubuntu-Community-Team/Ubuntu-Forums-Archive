---
title: "problem with tv as 2nd monitor"
date: 2014-01-02
forum: General Help
---

### Post by rejean on 2014-01-02
Hi all!
I am using  Ubuntu 12.04 with a GeForce 7600 video card connected to a JVC television set with a Svideo cable. 
I have no problem with my main monitor a LG Flatron w1942TQ but the screen of the tv set keeps refreshing itself (if that is the right term. I mean it is kind of rolling from top to bottom. 
I have no problem with PCLinuxOS or Mageia but with Ubuntu and Linux Mint I cannot figure it out.
Any suggestion anyone?

---

### Post by papibe on 2014-01-02
Hi rejean.

Check if Ubuntu is using the same monitor timings than PCLinuxOS.

Run this on both distros to check it (on a terminal open on the TV):
```
xvidtune -show
```
If they are not the same you can force the good PCLinuxOS' on Ubuntu by taking the timing data and using xrandr to create and set a new resolution (read [here]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html") for an example).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by rejean on 2014-01-02
I have a problem in PCLinuxOS;
```

[rejean@localhost ~]$ xvidtune -show
bash: xvidtune: command not found
[rejean@localhost ~]$ su
Password: 
[root@localhost rejean]# xvidtune -show
bash: xvidtune: command not found
[root@localhost rejean]# 


```

I'll reboot in Mageia and see what happens.

---

### Post by rejean on 2014-01-02
same thing in Mageia
but

```

[root@localhost rejean]# xrandr
Screen 0: minimum 8 x 8, current 2464 x 900, maximum 4096 x 4096
DVI-I-0 connected primary 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9*+   75.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     60.3     56.2  
   640x480        75.0     59.9  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
TV-0 connected 1024x768+1440+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   800x600        60.0  
   720x480        60.0  
   640x480        60.0  
   640x400        60.0  
DVI-I-2 disconnected (normal left inverted right x axis y axis)
DVI-I-3 disconnected (normal left inverted right x axis y axis)
[root@localhost rejean]# 

```

moving back in Ubuntu

---

### Post by rejean on 2014-01-02
Go figure!
After I started this thread and prior to your answer I installed a bunch of "nvidia" and that fixed the problem. I'll see if I can replicate it in Ubuntu LXLE.

---

