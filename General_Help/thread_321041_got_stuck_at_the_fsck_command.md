---
title: "got stuck at the fsck command"
date: 2006-12-18
forum: General Help
---

### Post by doromoji on 2006-12-18
Hi, found a lot of topic about edgy update, but I think my problem is different.
After updating, I open the machine for a few day.  Today I start my lovely ubuntu and found that the system got stuck at the fsck command 
```

* Activating swap... [OK]
* Checking root file system... [OK]
* Checing file systems...
fsck 1.39 (29-May-2006)
```

And then, nothing else happing.. no gdm, no shell, even the HD LED...
so, I don't know how to check for the error..
At first, I doubt about the HD problem, so I try booting windows(dual boot), try booting from CD, try mounting the root fs (/dev/hda2). Everything seems to be okay.

I try the fsck /dev/hda2. It runs for a second and no error message. However, I still cannot boot.

Once again, I try booting from CD, mount /dev/hda2 and change X driver to nv (hoping that it will be nvidia problem). However, it didn't resolve my problem.

Anybody can give me suggestion?

---

### Post by zek725 on 2006-12-18
the same thing happens to me. but fsck is stuck at 2.1%

---

### Post by doromoji on 2006-12-18
[http://ubuntuforums.org/showthread.php?t=307859]("http://ubuntuforums.org/showthread.php?t=307859")

This thread also talking about the same problem.  But I hope re-installation will be my last choice.

---

### Post by doromoji on 2006-12-19
Okay. I've some work around for this problem.

I've search through a lot of threads.  One of them says about some wierd cache after install nero burning rom in XP partition.  I've just had some experience with Nero7 in XP partition too.  So I try rebooting from the Edgy CD and disable mounting all windows partition.  Wonderfully, I can get my lovely Ubuntu again.

!! You needs to disable mounting ALL windows partition.

---

### Post by zek725 on 2006-12-19
:-k I removed my extra fat32 HDD thinking it was a hardware problem; then I got my box working when I deleted the entry of the automount of the fat32 drive in **/etc/fstab**.

First, I booted the recovery console which also took more than 10 minutes to finish the **Checking root file system...**. I left it for a few minutes then voila! **#root@ubuntu**. The cursor was blinking but when I attempted to type, no response. After a few seconds, it responded. \\:D/ Then, I edited the **/etc/fstab** and removed the entry of the suspected HDD.

---

