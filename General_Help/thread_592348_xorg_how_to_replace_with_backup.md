---
title: "xorg how to replace with backup"
date: 2007-10-26
forum: General Help
---

### Post by henryrollins on 2007-10-26
First off I confess I'm new to linux so take it easy on me.

  I've been experiencing issues with ubuntu correctly detecting the video resolution and refresh rates of my monitor.  To make a long story short after editing some values in the xorg file, x no longer starts.  

  I have a backup but I don't know how to replace the original with the backup especially since I don't even get to log in because it doesn't detect a screen.  

  I tried using a live cd to get in and replace the file with the backup but it tells me access denied.

HELP!

---

### Post by taurus on 2007-10-26
You can always boot into recovery mode from GRUB menu so no need to boot from the LiveCD.  Then at the prompt, do

```
cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```
_Assuming_ your backup copy is called **xorg.conf.bak**.

Then reboot and see what happens.

```
shutdown -r now
```

---

