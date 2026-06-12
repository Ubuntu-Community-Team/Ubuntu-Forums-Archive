---
title: "/etc/fstab changes in Edgy"
date: 2006-12-02
forum: General Help
---

### Post by wgscott on 2006-12-02
With the upgrade to Edgy, fstab now used UUID serial numbers instead of devices (like /dev/hdc1) to mount filesystems.

The idea I guess is to make the system more robust, so that your filesystem or partition will still mount if for some inexplicable reason the device name changes.

However, I found out the hard way that the new system may be buggy, at least in the context of my computer (a fairly recent custom job, i686).

Briefly, somehow disk arbitration was becoming confused and filesystems seemingly at random were being remounted as read-only.  I underwent some heroics (posted separately) and now that I have replaced the edgy /etc/fstab with the pre-edgy version (the upgrade kindly made the backup for me, suggesting someone somewhere knows this might be buggy or is uniquely conscientious) that uses devices instead of UUID numbers, it seems to be behaving normally again.

So here are my questions:

1. Why the change?   (Usually debian configuration prompts the user when a configuration file is to be changed, and defaults to leaving things as they are unless not backward-compatible.)

2. Was it tested?

3.  Is anyone else having problems?  Should I report this as a bug?

---

### Post by LLRNR on 2006-12-02
I don't know if it's a bug or weather you should report it or not... but here's something similar : [http://www.ubuntuforums.org/showthread.php?t=310748](http://www.ubuntuforums.org/showthread.php?t=310748)

So I just answered the first half of your third question. If you find the answers to Q1, Q2 and the second half of Q3, please let me know too, I'm running Edgy as well but it's a clean install and I'd like to know what I'm supposed to be expecting. :D

LLRNR

---

### Post by wgscott on 2006-12-02
Yeah, it is exactly the same problem.

It took four or five hours of my life that I will never have back.

---

### Post by odin1965 on 2006-12-03
My dapper install used UUID in fstab as well. When I installed it, I had an existing Mepis 3.0 install at hda3 that I eventually deleted after a few months of using 6.06. This caused boot up to stall and I almost had a heart attack. Had to ctrl+D to continue with booting every time. Looked at fstab and saw the UUID numbers and never found a suitable answer until today. All makes sense now. Same thing happened when I installed edgy on the partition that had Mepis, then deleted dapper afterwards. Have been kind of leary about playing with things in fstab but now I understand what whet wrong and have now fixed it. When I reformat a drive that is mounted by ubuntu I just have to 'sudo vol_id -u' and get the UUID then copy that over the old one in fstab, simple now.

---

