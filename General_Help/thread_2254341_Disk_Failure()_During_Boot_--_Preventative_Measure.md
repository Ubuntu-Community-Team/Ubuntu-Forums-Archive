---
title: "Disk Failure(?) During Boot -- Preventative Measures?"
date: 2014-11-26
forum: General Help
---

### Post by klundermann on 2014-11-26
My system had a near-death experience when booting today.  I got as far as the usual screen saying something like "/dev/mapper/cryptswap cannot be found" along with options to continue to wait, hit 'S' or hit 'M'.  What was unusual was that this message did not vanish after a few seconds.  After several minutes, I powered down, waited, and rebooted.  The same thing happened.  Then I hit 'M' and was dropped into a shell.  I tried running fsck but got the error message "/dev/sda6 is mounted -- e2fsck: Cannot continue, aborting."  I tried fsck a couple of more times with different options (-A and -s, I think).  Same result.  I then exited the shell.  To my amazement, the system then proceeded to boot normally, and I'm using it now to post this.  I gather that some sort of disk problem occured.  Two questions:  1. Is there anything I can do before shutting down to reduce the likelihood of a recurrence of the problem? 2. If the problem does recur, what should I do?  Thanks much....

---

### Post by lukeiamyourfather on 2014-11-26
Try disabling swap because that message means the swap partition couldn't be found when booting.

```
sudo swapoff -a
```

If that works fine it's possible the partition layout or drive arrangement has changed so swap is no longer where the system thinks it is. If there are other errors once swap is disabled it's possible the drive is dying or other hardware problems (cables, controller, power supply).

---

### Post by klundermann on 2015-01-04
A belated thank-you, lukeiamyourfather.  Your post helped me understand the problem better.

---

