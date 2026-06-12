---
title: "Screen Resolution Settings"
date: 2008-06-28
forum: General Help
---

### Post by homer454 on 2008-06-28
The only resolutions available to use in my HP Pavillion dv9823cl are 640x480 and 800x600. The native resolution is 1440x900. What are the terminal commands to set this? Or where may I go to get this resolution set?

---

### Post by kooldino on 2008-06-28
You want to edit your /etc/X11/xorg.conf file and specify the resolution in there.

I'm having a similar issue, however, for some reason my specifications are being ignored.

---

### Post by YaroMan86 on 2008-06-28
Try typing alt+f2 and then type in the following:

```
gksudo displayconfig-gtk
```

Explicitly define your monitor. If it isn't in your list there, choose a generic one that fits with your best possible resolution.

Automatic detection of monitors in Ubuntu is unreliable. This is a good way to fix it without mucking directly with /etc/X11/xorg.conf.

---

### Post by homer454 on 2008-06-28
Ok. I have it set. Thanks guys. :popcorn:

However, I'm having some trouble with my wi-fi.

Follow up in this post:
[http://ubuntuforums.org/showthread.php?p=5283114&mode=linear#post5283114](http://ubuntuforums.org/showthread.php?p=5283114&mode=linear#post5283114) 

:guitar:

---

