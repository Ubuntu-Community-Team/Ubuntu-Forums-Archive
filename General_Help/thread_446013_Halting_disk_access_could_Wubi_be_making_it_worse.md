---
title: "Halting disk access: could Wubi be making it worse?"
date: 2007-05-16
forum: General Help
---

### Post by PersistentLurker on 2007-05-16
**Note:** This issue has been **abandoned**.

I'm having a problem with my recently Wubi-installed Xubuntu 7.04 system. Hard disk access is unusably slow. It is characterized by strange, frequent, irregular pauses in disk access. Even stranger, CPU usage falls to near-zero during these pauses.

This thread contains my past troubleshooting attempts: [http://ubuntuforums.org/showthread.php?t=441764](http://ubuntuforums.org/showthread.php?t=441764)
To summarize: dmesg shows no errors. Changing the disk scheduler mode had no effect. The hard drive passes all diagnostic tests I've thrown at it. The halting is much worse when copying files than when reading a single file. Thermal halting in the CPU and timer interrupt issues have been ruled out as possible causes.

The question I have for you guys: could Wubi be involved in this problem, or making it worse?

If anyone has any ideas, I would greatly appreciate it. Thanks!

---

### Post by ago on 2007-05-16
Make sure your windows folder is not compressed and defragmented. If the probelm remains you may want to use the release that is coming up shortly.

---

### Post by PersistentLurker on 2007-05-17
Thanks ago.

The partition I was using for Wubi was indeed heavily fragmented. After two passes with JkDefrag still left it quite fragmented, I moved the Wubi install into a separate, empty partition and ensured that it was fully defragmented.

I don't think the disk is compressed, I've never seen any references to disk compression on this system, but I haven't checked for sure. I'll report back once I'm sure.

Disk access under Xubuntu has improved significantly - OpenOffice start time is down 40%. But it is still far worse than what I get under WinXP and Topologilinux (which has recently been installed in the same partition as Wubi resides on now). I am still getting the strange pauses

The thing that bothers me is this: why would these pauses occur? During the pauses, the CPU isn't doing anything, the hard disk heads aren't doing anything. What could the system be waiting for?

---

### Post by ago on 2007-05-18
> **PersistentLurker said:**
> The thing that bothers me is this: why would these pauses occur? During the pauses, the CPU isn't doing anything, the hard disk heads aren't doing anything. What could the system be waiting for?

Try to pre-allocate the images. A way to do that is to cut and paste them back and forth to/from another partition. Then defrag. Then install.
Also check in topologilinux what module is actually used for your HD/controller.

---

### Post by PersistentLurker on 2007-05-18
> **ago said:**
> Try to pre-allocate the images. A way to do that is to cut and paste them back and forth to/from another partition. Then defrag. Then install.

OK, I'm not sure I quite follow. Please tell me if this is the correct procedure:
(C: is the drive Wubi was originally installed on. D: is the near-empty one were Wubi has been moved to.)
[LIST=1][*]Move the images from D: to C:
[*]Move the images from C: to D:
[*]Defragment D:
[*]Delete the images
[*]Install Wubi on D:
[/LIST]

What does "pre-allocate" mean anyway? How is it different from ensuring that the images are defragmented (I can assure you, they are completely defragmented now)? Is the idea that we start out fresh with defragmented images rather than starting with fragmented ones and defragging them later? Or is it something else were are trying here?

It should be noted that the initial improvement in disk performance after defragging seems to have been illusionary. Now, after some uptime, disk performance seems to be worse than ever before; OpenOffice start time is now more than double the time required before defragging. D: is further down the disk than is C:, but still ...

I'll check on what driver Topologilinux is using and report back. Thanks again for your help.

---

### Post by ago on 2007-05-18
[LIST=1]
[*]Install Wubi on D: (do not reboot)
[*]Move the images from D: to C:
[*]Move the images from C: to D:
[*]Defragment D:
[*]Reboot and continue installation
[/LIST]

---

### Post by PersistentLurker on 2007-05-18
> **ago said:**
> [LIST=1]
[*]Install Wubi on D: (do not reboot)
[*]Move the images from D: to C:
[*]Move the images from C: to D:
[*]Defragment D:
[*]Reboot and continue installation
[/LIST]

OK, I did that. The disk halting is still occurring, only slightly better than it was on the first fragmented install in C:.

As for what driver Togologilinux is using, I can't seem to identify a specific driver. What I can say is that unlike [X]ubuntu, Togologilinux is using the traditional IDE drivers (the ones that create /dev/hd* devices).

---

