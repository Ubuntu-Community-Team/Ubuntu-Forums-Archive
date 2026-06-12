---
title: "GRUB gone"
date: 2007-05-31
forum: General Help
---

### Post by CocoAUS on 2007-05-31
My sister tried installing Fedora 7 (I think on a separate drive) from Ubuntu Feisty.  When she rebooted, neither OS would load.  Looking at the Ubuntu drive with the livecd, there's no grub.conf file or anything.  I don't know exactly what happened or what it looked like when she tried to boot, but how would we fix this?  Is there a way to reinstall GRUB from the livecd, or to simply add a grub.conf file?  Thanks.

---

### Post by kefir on 2007-05-31
This might solve it

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by merlinus on 2007-05-31
Boot from any live cd.

In a terminal:

```

sudo grub
find boot/grub/stage1
root (hd0,7)
setup (hd0)
quit

```

substitute your results for find on the next two lines.

hth....

-merlin

---

### Post by CocoAUS on 2007-05-31
Thanks much for the help, guys.

---

