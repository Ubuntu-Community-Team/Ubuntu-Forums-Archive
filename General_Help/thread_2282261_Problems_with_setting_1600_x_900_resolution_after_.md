---
title: "Problems with setting 1600 x 900 resolution after reboot"
date: 2015-06-12
forum: General Help
---

### Post by Justin_Large on 2015-06-12
On my Ubuntu 14.04 System76 machine, I've been making attempts to set my resolution to 1600 x 900.  Since this resolution isn't offered in the dropdown in Displays, I use the following document:  [http://askubuntu.com/questions/330293/how-do-i-set-a-monitor-resolution-that-is-not-available-in-the-display-settings](http://askubuntu.com/questions/330293/how-do-i-set-a-monitor-resolution-that-is-not-available-in-the-display-settings).  Based on my results of running cvt 1600 900 60, I run the following command...

```
xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
```

However, this fails with the following...

```

X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  35
  Current serial number in output stream:  35

```

Anything I can do to get past this?  Also, are there any plans to simply add the 1600x900 option in the dropdown in Displays?  I'm currently on the default of 1920x1080, but I'm finding that to be too small.

---

