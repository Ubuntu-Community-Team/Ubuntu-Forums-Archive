---
title: "USB Printer : too many levels of symbolic links"
date: 2006-12-07
forum: General Help
---

### Post by jibe74 on 2006-12-07
Hello,

After a lot of unsuccessful tries to install a Samsung CLP-510 (USB) printer, I tried to install it again with the help of [this tutorial]("http://ubuntuforums.org/showthread.php?t=239405"). As I did not have the directory /usr/share/ppd/linuxprinting.org-gs-builtin/ in my computer, I put CLP-510splc.ppd in /usr/share/ppd/Samsung/. I also changed x86_64/at_root/usr/lib64/ to i386/at_root/usr/lib/ and all /usr/lib64/ to /usr/lib/, as I am using a Pentium IV.

Unfortunately, I was not able to install the printer (even if it was well-detected by gnome-add-printer tool), I put CLP-510splc.ppd again in  /usr/share/ppd/linuxprinting.org-gs-builtin/ which I created for just for that.

As I found out that the printed was not detected anymore by gnome-add-printer tool, I tried to restart udev and cupsys, but that did not detect the printer either.  So, I tried a reboot, and found the pilot under Samsung (but not under linuxprinting..., invisible in the list of manufacturers!!!) and it seemed that installation ended successfully.

But the test page did not work, I just realized that the printer was at PAUSE, and it's impossible to activate it : again, it paused by itself after two or three seconds!!! Later, I discovered in the cups web interface the message below appears:

```
usb:/dev/usb/lp0 : too many levels of symbolic links
```

Any ideas to solve this problem (or to properly install this printer) ?

---

### Post by jibe74 on 2006-12-08
Hi,

I don't like the way I did : redefine the printer port, when the printer was detected on this port before... Could it be the problem ?

But how can I do ? Why the printer is no more detected when I just made a copy of CLP-510splc.ppd to have it in the /usr/share/ppd/linuxprinting.org-gs-builtin/ folder ? :-k

---

### Post by jibe74 on 2006-12-10
Hello,

Nobody has an idea or can advice something to check ?
:(

---

