---
title: "Resolution problems again..."
date: 2012-12-22
forum: General Help
---

### Post by jclmusic on 2012-12-22
Hi everyone. I recently had a monitor go bad:
[http://ubuntuforums.org/showthread.php?p=12409284#post12409284](http://ubuntuforums.org/showthread.php?p=12409284#post12409284)

I now have a new monitor and no longer have the purple tint, but I am still being limited to a resolution smaller than what my monitor is capable of. Both my old and new monitors are capable of 1440x900, but with the old one that went bad, I was limited to 1024x768 and now with this new one I'm being limited to 1360x768.

Any idea how I can get the proper resolution?

---

### Post by Petro Dawg on 2012-12-22
I have an integrated AMD graphics chip and can access the AMD Catalyst Control Center by the following terminal code.

```
gksudo amdcccle
```From there, screen resolution settings can be changed.

However,  (in the likely case that you do not also have AMD graphics) you will probably need to let us know which graphics chip and/or drivers you are using. 

Edit...
I just read your old thread.  Are you still not able to change resolution with...
```
gksudo nvidia-settings
```
?

---

### Post by jclmusic on 2012-12-22
Sorry I should have said. 
I have a GeForce 8400 GS video card.
The maximum for this card according to a google search is 2048x1536, but I'd be content with just being able to get 1440x900.

---

### Post by jclmusic on 2012-12-23
> **Petro Dawg said:**
> 
Edit...
I just read your old thread.  Are you still not able to change resolution with...
```
gksudo nvidia-settings
```
?

Nope, I can only change it to 1360x768 or lower.

---

### Post by Pjotr123 on 2012-12-23
Try xrandr:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by jclmusic on 2012-12-23
> **Pjotr123 said:**
> Try xrandr:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Getting errors on this command:

```
dusepo@dusepo-desktop:~$ xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
xrandr: Failed to get size of gamma for output default
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  19
  Current serial number in output stream:  19

```

---

### Post by jclmusic on 2012-12-23
bump

---

### Post by jclmusic on 2012-12-29
My new monitor that I bought is now starting to flicker a purple shade at times!! I am worried that some new drivers or whatever is causing this problem is making my monitor not be recognised properly and in turn sending an incorrect signal that is damaging my monitor!

---

