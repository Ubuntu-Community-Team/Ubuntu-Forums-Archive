---
title: "windows partition hda1 appears blank"
date: 2007-03-05
forum: General Help
---

### Post by bishman on 2007-03-05
Hi all,

I dual boot ubuntu and XP and mainly use ubuntu for surfing the web. Most of all, i'm lovin it...

However, when I logged on to ubuntu this morning, my windows partition (hda1) which is normally on my desktop has disappeared. And if I
cd /media/hda1
the directory exists. But when I
ls
it appears blank (as in nothing is returned)
I would do these instructions: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) but worried it might make it worse as this has happened randomly, even after another reboot, and was working fine before.

Any ideas?

---

### Post by aa.ivanov on 2007-03-05
are you sure hda1 is mounted?

on command line you can type 'mount' to see mounted filesystems, or alternatively you can check System > Administration > System monitor (or whatever it's called in English) to see the filesystem mounted.

---

### Post by bishman on 2007-03-06
Thanks for that.

I can't imagine how it unmounted. But after disabling / enabling write support with NTFS-3g config tool, then

sudo mount -a

seemed to do the trick.

Cheers very muchly! :)

---

### Post by bishman on 2007-03-16
It seems to be a problem if windows doesn't shut down properly the last time you use it (which was by accident anyway), so if it doesn't doesn't unmount from the windows session, you can restart windows and shut down properly. Then it should work

---

