---
title: "Blank Screen after booting ubuntu 7.10"
date: 2008-03-15
forum: General Help
---

### Post by cmohjo on 2008-03-15
I recently updated to ubuntu 7.10 on a dell laptop and dual boot with XP. everything worked great until updating to 7.10. Now when I boot, ubuntu opens to a blank screen. I can hear the drums and can still type in user name and hear the os working, screen is just blank.

The same issues occur when booting in recovery mode, I'm confused cause my system never had any isues befor 7.10.

Please Help, ive read the oter posts and still having these problems.

---

### Post by Rocket2DMn on 2008-03-15
Have you reconfigured X yet? - see here: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

---

### Post by cmohjo on 2008-03-15
Just did that, still have a blank screen?

Any other advice or ideas would be great, thanks for the help

---

### Post by Rocket2DMn on 2008-03-15
What is your video card make/model and what driver did you select when reconfiguring X?  If possible, post your xorg.conf file:
```
cat /etc/X11/xorg.conf
```

---

### Post by cmohjo on 2008-03-16
Video card is Mobility Radeon 7500c and i chose the ati.

---

### Post by Rocket2DMn on 2008-03-16
Try again, but use "vesa" driver.  Your card is rather old and may just have horrible support, this way we can at least get into the GUI.

---

### Post by zxscooby on 2008-03-16
I have that card , it realy stinks. 
i use the open source ati driver as it does not work with fglrx.
Seems to me like it could be a problem with your monitor settings as it is loading the desktop
and playing the sounds. Most of the time if its the graphics card and driver you will get an error
at login.  Does it show the boot menu? If not ,check to see if your display settings are correct in the bios , it could be set to an external monitor or pci vs. agp or vise versa.

---

