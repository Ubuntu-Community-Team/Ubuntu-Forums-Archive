---
title: "Turn off/disable touchscreen"
date: 2014-06-21
forum: General Help
---

### Post by josephellengar2 on 2014-06-21
Hi there!

I'm running Ubuntu 14.04 on an HP Envy touchscreen notebook. I'm using Cinnamon DE, but I don't think that matters. 

I hate touchscreens. I touch the screen accidentally or wipe off some grit and the computer does something weird. Is there any way to disable it? Or are there drivers that I could just uninstall? I've surfed around and haven't found anything more recent than 2012 or so.

Thanks!

---

### Post by 3rdalbum on 2014-06-21
I can't give you a precise answer, but I can give you two different ways I would approach this problem.

1. Find out the name of the driver module that runs the touchscreen, and then add it to the 'blacklist.conf' so it doesn't load.

2. If you can't figure out which module it is, take a look in your /etc/X11/Xorg.conf and comment-out the Input subsection that defines the touchscreen as an input device.

---

### Post by josephellengar2 on 2014-06-21
> **3rdalbum said:**
> I can't give you a precise answer, but I can give you two different ways I would approach this problem.

1. Find out the name of the driver module that runs the touchscreen, and then add it to the 'blacklist.conf' so it doesn't load.

2. If you can't figure out which module it is, take a look in your /etc/X11/Xorg.conf and comment-out the Input subsection that defines the touchscreen as an input device.

How would I go about finding out the modules? I actually have no /etcX11/Xorg.conf file.

---

### Post by oleg-sigida on 2014-07-13
> **josephellengar2 said:**
> How would I go about finding out the modules? I actually have no /etcX11/Xorg.conf file.

check out this topic:
[http://ubuntuforums.org/showthread.php?t=2209083&p=12945855#post12945855](http://ubuntuforums.org/showthread.php?t=2209083&p=12945855#post12945855)

---

### Post by josephellengar2 on 2014-07-13
> **oleg-sigida said:**
> check out this topic:
[http://ubuntuforums.org/showthread.php?t=2209083&p=12945855#post12945855](http://ubuntuforums.org/showthread.php?t=2209083&p=12945855#post12945855)

Thanks! That worked.

---

