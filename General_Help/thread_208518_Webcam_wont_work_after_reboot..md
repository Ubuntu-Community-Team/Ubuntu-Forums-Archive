---
title: "Webcam wont work after reboot."
date: 2006-07-03
forum: General Help
---

### Post by Rackerz on 2006-07-03
I used this topic to install the driver for my quickcam messenger ([http://www.ubuntuforums.org/showthread.php?t=126053&highlight=quickcam+messenger](http://www.ubuntuforums.org/showthread.php?t=126053&highlight=quickcam+messenger)) and it works perfect except after I reboot, it wont load the driver at boot up, so how do I do it? I've tried all the scripts and things in that post but they just don't work. Below is some information I got from the installer.

[quote]=== Entering root mode ===
/usr/bin/install -c -D -m 644 quickcam.ko        /lib/modules/2.6.15-25-386/misc/quickcam.ko
/usr/bin/install -c -D -m 755 qcset /usr/local/bin/qcset
/sbin/depmod -a
=== Leaving root mode ===
Hopefully the driver is now installed and can be loaded
with command
        modprobe quickcam
as root. You can put this command into some startup
script to do it always automatically at boot.
The exact location depends on distribution, and this
script is yet too dumb to do this automatically.[.quote]

I hope someone can help, thanks.

---

### Post by Rackerz on 2006-07-03
Bumper.

---

