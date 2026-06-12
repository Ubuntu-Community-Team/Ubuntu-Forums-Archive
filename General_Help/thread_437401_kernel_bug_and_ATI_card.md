---
title: "kernel bug and ATI card"
date: 2007-05-08
forum: General Help
---

### Post by Jim D v2.0 on 2007-05-08
I've been banging my head against the wall for two weeks now trying to get my ATI carg to do the 3d graphics, I finally tracked my problem to this.

here is the salient error from /var/log/Xorg.0.log from my fiesty install.
> (EE) fglrx(0): GART is not initialized, disabling DRI
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

According to this [link]("https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684")  this is due to a know bug in the kernel involving certain chip-sets.

Does anybody know of a work-around for this problem? If not I am going to have to revert to edgy and perhaps windows:mad: .

---

### Post by IgnorantGuru on 2007-05-09
When I researched this problem (which also occurs with Edgy), I found lots of complaints but NO solutions - seems to be a bug in the driver, and rumor has it ATI is not planning to support those cards further.

Here are my bookmarks if you want to check the latest developments (last I looked was a few months ago).  Please let me know if you find a solution.  (Not all these links may be helpful or relevent - just what I saved on the subject.)

[https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/68739](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/68739)
[http://forums.gentoo.org/viewtopic-t-533354.html](http://forums.gentoo.org/viewtopic-t-533354.html)
[http://forum.ubuntu-fr.org/viewtopic.php?pid=642740](http://forum.ubuntu-fr.org/viewtopic.php?pid=642740)
[http://en.opensuse.org/ATI_Driver](http://en.opensuse.org/ATI_Driver)
[https://bugzilla.novell.com/show_bug.cgi?id=222993](https://bugzilla.novell.com/show_bug.cgi?id=222993)
[http://ubuntuforums.org/showthread.php?t=356741](http://ubuntuforums.org/showthread.php?t=356741)

---

### Post by Jim D v2.0 on 2007-05-10
> **IgnorantGuru said:**
> When I researched this problem (which also occurs with Edgy), I found lots of complaints but NO solutions - seems to be a bug in the driver, and rumor has it ATI is not planning to support those cards further.


Interestingly, I did not have this problem in edgy, apparently others did.

---

