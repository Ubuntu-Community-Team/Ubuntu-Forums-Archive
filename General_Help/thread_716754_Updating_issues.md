---
title: "Updating issues"
date: 2008-03-06
forum: General Help
---

### Post by randoy on 2008-03-06
I got a problem.

Woke up and did 3 automatic updates today and my computer froze.  I restarted and it brought me to something that said "an automatic filesystem check of the root filesystem failed".

The updates were all for the Evolution mail client (if that helps).  I haven't tried much yet because I'm not really sure what to try.  My OS is Gutsy Gibbon, 7.10.  Any help would be greatly appreciated.

Edit : Fixed it =P

From command line typed in "sudo fsck /dev/sda1" and it corrected alot of errors.  After that I rebooted and was back to my desktop environment.  Thanks!

---

### Post by taurus on 2008-03-06
It should drop you into a shell after it shows you that error message.  You need to run fsck of your root parition, /, by hand.

```
fsck -y /dev/sda1
```
Assuming /dev/sda1 is where / is.

---

