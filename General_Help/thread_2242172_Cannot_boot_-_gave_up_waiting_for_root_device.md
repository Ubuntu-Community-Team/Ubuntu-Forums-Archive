---
title: "Cannot boot - gave up waiting for root device?"
date: 2014-08-31
forum: General Help
---

### Post by sharks706 on 2014-08-31
EDIT: Nevermind, I fixed it
EDIT2: It's not fixed, I added some more info at the bottom

So I had Ubuntu 14.04 installed and working fine, until today when i decided to install Windows 7.  I re-installed the grub using boot repair, since windows had wiped it out, but now Ubuntu will not boot up, instead giving me this error message

Gave up waiting for root device.  Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay = (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/"uuid" does not exist
Dropping to a shell!

I tried editing the menu entry in the grub 2 menu, changing root=UUID=<long number>" to "root=/dev/sdXY", but that only results in many error messages and finally a black screen

Update:  After editing the menu entry, Ubuntu finally loaded somehow, but only once. After restarting, I only get the message "The disk drive / is not yet present", followed by "The disk drive /tmp.." if I press s to skip.  Where to go from here?

Here's the pastebin from boot repair: [http://paste.ubuntu.com/8193408/](http://paste.ubuntu.com/8193408/)

Please help
thanks

---

### Post by cariboo on 2014-08-31
In response to your report, why not post how you solved the problem, so that others may benefit from your experience.

---

### Post by sharks706 on 2014-08-31
Unforuntately, my claim was premature... I thought I had solved the problem because after editing the menu entry for the sixth time, ubuntu finally loaded, but I was unable to replicate this one-time success.  After restarting, I only get the message "The disk drive / is not yet present", followed by "The disk drive /tmp.." if I press s to skip.  I don't know what to do now, help?

---

