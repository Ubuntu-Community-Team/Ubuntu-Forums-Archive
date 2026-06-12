---
title: "Unable to autostart services running Ubuntu 15.10 under Android TV"
date: 2015-11-30
forum: General Help
---

### Post by Kevin_Townsend on 2015-11-30
First a little background:
 My Ubuntu Linux environment is far from normal. In the interest of replacing my Home Theater PC I procured an "Nvidia Shield TV" box. It is an incredibly powerful Android Lolipop based device which functions very well as both a media player and gaming device. However, it functions very poorly as a media server and download box. To augment these capabilities I have used an android package called Linux Deploy which uses busybox to install and run various Linux distributions in the background under android. I successfully used it to install Ubuntu 15.10

My problem:
While I was able to successfully install and start several sysvinit services, I can't seem to get them to boot when Linux Deploy starts Ubuntu. 
I understand that Ubuntu 15.10 traditionally uses systemd, however I think that it's running under android is complicating matters.

For example when I look at PID 1 I see it is running /init which would indicate linux booted using System V. (I suspect this is for android)

The files and directories for systemd still exist but when I attempt to run systemctl I get the error
Failed to get D-Bus connection: Operation not permitted.
I suspect this is because Ubuntu is started in a chroot environment but I'm not savvy enough to know what to do about it.

If I could find a Linux Deploy support forum I'd inquire there, but sadly I cannot. If any of you can help I'd appreciate it.

---

### Post by Kevin_Townsend on 2015-11-30
I found the problem. Apparently this is a common issue for chrooted environments that are started under system v.  Fortunately there was an option with the Linux Deploy android app that I had previously failed to identify to enable and add custom scripts.  I did this and reconfigured and now my services start when Ubuntu does. Hope this helps someone else.

---

