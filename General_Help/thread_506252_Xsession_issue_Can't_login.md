---
title: "Xsession issue? Can't login"
date: 2007-07-21
forum: General Help
---

### Post by sunol on 2007-07-21
[COLOR="Red"]Solved! [/COLOR]This post pointed me in the right direction
[http://ubuntuforums.org/showthread.php?t=482406&highlight=failsafe+gnome](http://ubuntuforums.org/showthread.php?t=482406&highlight=failsafe+gnome)

Noobie help needed.
I just installed a new driver for my usb wireless. Using this thread:
[http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73)

Everything seemed to be working great. Then I restarted the computer and now I can't login. No error message, it just keeps flipping back to the unsername prompt.

My home directory is not full and I can log in to terminal using ctrl+alt+F1 without a problem. Just can't seem to get into a gnome session.

Thanks!
Mike

---

### Post by diepruis on 2007-07-22
> **sunol said:**
> My home directory is not full and I can log in to terminal using ctrl+alt+F1 without a problem. Just can't seem to get into a gnome session.

I've had this error a few times. This occurs when Linux can't mount the partition that stores your home directory. Since it can't get at your GNOME config files in that case, the whole GUI comes crashing down. Try executing

```

sudo mount -a
sudo /etc/init.d/gdm start

```

If it gives any error messages, please post them. If there are none, but this still doesn't work, the output of "mount" and your /etc/fstab file would be welcome.

In my case, this occurs when my SATA drives' cables fall out (yes, they fall out ^_^). You might want to check whether your drives are still connected.

---

