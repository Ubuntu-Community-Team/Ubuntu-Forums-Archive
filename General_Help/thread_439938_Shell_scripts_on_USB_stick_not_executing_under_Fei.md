---
title: "Shell scripts on USB stick not executing under Feisty"
date: 2007-05-11
forum: General Help
---

### Post by igoddard on 2007-05-11
I have a USB stick with software set up under Edgy.  After upgrading I have tried to execute one of them as owner (in fact execute permission is set for all users).  If I have an interpreter line, e.g. #!/bin/sh at the start it fails with the response "bash: ./oxygen.sh: /bin/sh: bad interpreter: Permission denied"

If I comment out the interpreter line I simply get "bash: ./oxygen.sh: Permission denied".

Even a simple one line script to echo a response back has the same result - what will run from my home directory won't run from a directory on the USB stick.  Not even as root.

Any ideas?

Ian

---

### Post by Wim Sturkenboom on 2007-05-11
USB mounted without execute permission? Not sure how to set it.

---

### Post by igoddard on 2007-05-11
Yup, you're right.  mount shows it as noexec.  If I umount and mount from root without noexec it works.  Now I have to work out where the mount is configured.

Ian

---

### Post by reclusivemonkey on 2007-05-11
I *think* you might find this option in the Preferences, under the "Removable Drives and Media" section, althoug I am at work right now so can't check this. I have a USB stick and it executes scripts fine, I even run them as the USB drive is plugged in, although I do get a dialog to check I want to do this.

---

### Post by Wim Sturkenboom on 2007-05-11
> **igoddard said:**
> Now I have to work out where the mount is configured.This info might be outdated and not apply to Ubuntu but you can try */etc/fstab*.

---

### Post by igoddard on 2007-05-11
Well, it's fixed but I'm not sure how!

Following reclusivemonkey (Triangle?  That makes you a neighbour; I'm in Holmbridge) I logged in using Gnome (normally KDE).  Not in Preferences>Removable...   but the properties available on the icon are more extended than in KDE.  The mount options in the Volume tab were empty so I pasted in the existing set as seen by mount except for the noexec.  It objected to an illegal option (not sure why, maybe it wants a space separated list instead of comma separated) but after clearing them it seemed to mount without the noexec under both managers.

That's the short version.  There was a lot of faffing about with mount points as well as Edgy was originally set up to use /media/usbdisk, as were the scripts and Feisty wanted to use /media/disk.  I eventually discovered that the automounting doesn't like having the mount-points pre-exist.

BTW there isn't and wasn't an /etc/fstab entry - that would be too easy!  It must all be stored somewhere but I haven't found it yet.

Thanks to both of you.

Ian

---

### Post by reclusivemonkey on 2007-05-11
> **igoddard said:**
> 
BTW there isn't and wasn't an /etc/fstab entry - that would be too easy!  It must all be stored somewhere but I haven't found it yet.


Nope, as mounting of removable drives is done by udev, its all hidden away somewhere in /etc. You can tweak these rules but they aren't particularly user friendly.

Glad you got it working.

---

### Post by Cows on 2007-05-27
Yes I just had a problem with this a few minutes ago when I wanted to use my own debian installation scripts. Im 99% sure that the problem was that I had the USB Disk inserted while the debian installed the OS. So since it was mounted it was automatically added to the /etc/fstab. What I did to fix it was simple. Go into fstab and delete the flash drive mount point line completely. Make sure that you umount the flash drive before you do this. Then if the flash drive was mounted before and you just unmount chances are that it already has a folder. For me the folder was /media/usb0. So all you have to do is 

```
sudo mount /dev/sdb1 /media/usb0
```

Well that was my mount point. Just change sdb1 to w/e your usb drive's mount point is.

---

