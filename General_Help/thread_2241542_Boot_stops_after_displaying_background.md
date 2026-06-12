---
title: "Boot stops after displaying background"
date: 2014-08-26
forum: General Help
---

### Post by paperpilot-earthlink on 2014-08-26
I have had Ubuntu 14.04 running since May and now it stops booting after displaying the background photo.  I rebuilt the Grub using the Boot Repair Disk without improving the boot.  The results of that effort can be found here: [http://paste.ubuntu.com/8152198](http://paste.ubuntu.com/8152198)  There are several advanced options, but I don't know which to try.  Should I restore the MBR?  If so which type?  I'm out of my depth here.

---

### Post by grahammechanical on 2014-08-26
The boot loader (Grub) just loads the Linux kernel and then it no longer plays a part in loading Ubuntu. I do not think your problem was with Grub. Boot Repair tries to fix boot loader problems. Boot Repair is not qualified to fix OS loading problems.

As far as I can tell your OS is loading up to the Login screen. Is that correct? Do you have Ubuntu set to automatically log in? What background photo are you talking in about? Is it the background image (wallpaper) of the log in screen? Or the background image (wallpaper) of the desktop? Are you gett ing to a desktop but without the top panel and the Launcher?

Regards

---

### Post by paperpilot-earthlink on 2014-08-27
Thanks for your reply.

I get past the login but no top panel or Launcher.  The Boot Repair has options to Repair file systems and Purge kernels and reinstall last kernel.  Are these possible solutions?  I don't want to make the system worse than it is.

---

