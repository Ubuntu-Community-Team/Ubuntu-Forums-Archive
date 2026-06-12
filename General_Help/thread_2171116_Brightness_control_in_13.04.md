---
title: "Brightness control in 13.04"
date: 2013-08-29
forum: General Help
---

### Post by Abdul_Basith on 2013-08-29
I was using ubuntu 10.10 for long time, there also I had a brightness control problem in my laptop. By editing /etc/X11/xorg.conf it's fixed. Now I upgraded to 13.04, on this even after adding enable brightness in xorg, brightness control is not working. From other posts, I tried all combinations in /etc/default/grub, update grub and restart. None of the combination are working. My laptop model is lg r480, having nvidia g105M graphics card. Can anyone please give me a solution for this.

---

### Post by sbnwl on 2013-08-29
Do this exercise first and see if it works temporarily.
Open a terminal then enter these commands:

```
sudo su
```

Enter your password when asked.

Then enter this command

```
echo 1000 | tee /sys/class/backlight/intel_backlight/brightness
```

You should immediately see a change in brightness... Check this first.

---

### Post by 123com2 on 2014-04-09
> **sbnwl said:**
> Do this exercise first and see if it works temporarily.
Open a terminal then enter these commands:

```
sudo su
```

Enter your password when asked.

Then enter this command

```
echo 1000 | tee /sys/class/backlight/intel_backlight/brightness
```

You should immediately see a change in brightness... Check this first.

put line in  **/etc/rc0.d  **with editor an it will start up automatic.

---

### Post by Toz on 2014-04-09
> **123com2 said:**
> put line in  **/etc/rc0.d  **with editor an it will start up automatic.
Ummm, no. 

First of all. /etc/rc0.d is a directory, not a file. 

Secondly, runlevel 0 is for shutting down, so even if you created a file in that directory, it would not work. The proper location _is_ /etc/rc.local for entering a command to manually adjust brightness during system startup.

---

