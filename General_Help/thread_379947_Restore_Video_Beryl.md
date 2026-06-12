---
title: "Restore Video Beryl"
date: 2007-03-09
forum: General Help
---

### Post by siciliancasanova on 2007-03-09
I just tried to install beryl and got to the point where I was updating the nvidia driver.  (now realize that I didn't need to, mine was just fine) and after the system made the change it told me to restart.  I did and now it's not reading the video card.  It takes me to the all black terminal, and I can log in there.  Is there a command to restore the settings from there?  I'm so new to the command line that I would need some detail if possible.

---

### Post by ~LoKe on 2007-03-09
Try...
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by siciliancasanova on 2007-03-09
Ok that got me the screen where I choose the driver.  After I selected the driver it's outputting:> xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20070308200446

What do I need to input in response?

---

### Post by ~LoKe on 2007-03-09
You should be able to just hit enter, if not, "y".

---

### Post by siciliancasanova on 2007-03-09
Actually just found out I need to install the driver since it's a built on video card.  I'm going to download it and burn it on here.  Now I guess I need to know how to install a driver from a cd in the shell and also turn it on.

---

### Post by ~LoKe on 2007-03-09
If you still have Internet access and the use of the terminal, just type this in exactly:

```
wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run
```

Once it finishes:
```
sudo sh *9755*
```
It'll bring up a step by step installer, it's straight forward and can't be screwed up.  The last step will ask if you want it to reconfigure xorg.conf for you, if you haven't made any important modifications (dual monitor setup, etc) choose yes.

After that:
```
sudo /etc/init.d/gdm restart
```

---

### Post by siciliancasanova on 2007-03-09
It's resolving the domain but bringing up a 404 error, I typed it several times, monitor next to monitor.  Also, do I want to be trying to screw around with nvidia.  I was just on hp live chat and she told me that the exact specs for the onboard video card I have is an intel.  Now that list of drivers had nothing Intel.  I did have four that started with an "i" , like "i128" she told me to install a driver and gave me a link and I've put it on a disk, it's a .exe file.

---

### Post by ~LoKe on 2007-03-09
Intel; can't help ya there.

---

### Post by siciliancasanova on 2007-03-09
Since I just got ubuntu Installed, is there a way to reformat it and reinstall it?  I won't be losing any data so that's not my concern.  Thanks for helping me out btw.

---

### Post by ~LoKe on 2007-03-09
Of course!  Just pop the CD back in and do it all over again. :lolflag:

---

### Post by siciliancasanova on 2007-03-09
Thanks :)  Now it's time for my second cup of ubuntu.

---

