---
title: "Weird random &quot;Error splicing file&quot; error that kills my system"
date: 2018-12-07
forum: General Help
---

### Post by stinktier2 on 2018-12-07
I get the weirdest serious error on my current Xubuntu 18.04 system, especially when I try to copy large amounts of files (GB-wise) from one harddisk/ssd to another harddisk/ssd (which both are Linux-formatted). But the error can also happen when no copying is involved, but some file writing is done in the background.

So, for example, I want copy a large folder of dozens of GB (but the error can also show up when copying much smaller amounts) from my main disk to the second harddisk. While copying the following error message pops up:
[CENTER][FONT=courier new]Error splicing file
Input/output error
Do you want to skip it?[/FONT]

[/CENTER]
From this moment on my system is shot. I lose all permissions to write on my main harddisk, which makes the system unstable and is only remedied by rebooting. This has to be done as quickly as possible, else I won't even have permission to reboot or to do any other actions.

Normally, this error seems to mean that the storage hardware (hd or ssd) is faulty. However, when I open the "Disk" tool all disks are assessed as OK (also in S.M.A.R.T. data). All my disks are rather new with my main disk a Samsung Evo Pro 850 and I am surprised that it should fail after only a couple of months of desktop use.

Even stranger is, that I can copy the files without a problem when I choose to copy them in smaller batches or one by one with no error message. And when I copy the files again in bulk from this second harddisk to a third harddisk the error can show up and the system is shot again. It doesn't matter which disk is the source and which is the destination... somehow I get the "error splicing file" error that kills my system – but only some of the time and usually only when large data is read/written.

Since the error seems so random, is there something I can do? How can I make sure it is really a hardware problem? I don't want to go through the hassle of buying a new ssd and setting up a new system if there is a possible easier solution to an underlying OS/software problem.

---

### Post by spjackson on 2018-12-08
I would suspect faulty RAM. It would be worth running memtest to either confirm or rule it out.

---

### Post by stinktier2 on 2018-12-10
I just did one full pass of Memtest through my 16GB RAM from a LiveCD with default settings and no errors were found. Should I let run Memtest for longer or change its settings and run again?

There error still occurs, by the way...  :sad:


Edit: I removed first one, then the other RAM module and so booted my pc with half of its memory. And still this "error splicing file" thing is easily reproduced when I try to copy large folders. So it seems that the RAM is not at fault? I will try later with different modules in case both of my modules are shot, but I guess that this is unlikely (especially since Memtest doesn't find anything).

---

### Post by westie457 on 2018-12-10
Check the inodes of the SSD and post the results here. The commands are df -h and df -i to be run separately.

---

### Post by stinktier2 on 2018-12-10
> **westie457 said:**
> Check the inodes of the SSD and post the results here. The commands are df -h and df -i to be run separately.
Okay.

```
**df -h**
Filesystem                    Size  Used Avail Use% Mounted on
udev                          7,8G     0  7,8G   0% /dev
tmpfs                         1,6G  1,4M  1,6G   1% /run
/dev/mapper/xubuntu--vg-root  220G  178G   31G  86% /
tmpfs                         7,9G     0  7,9G   0% /dev/shm
tmpfs                         5,0M  4,0K  5,0M   1% /run/lock
tmpfs                         7,9G     0  7,9G   0% /sys/fs/cgroup
/dev/sda1                     472M  165M  284M  37% /boot
tmpfs                         1,6G   16K  1,6G   1% /run/user/1000
```

```
**df -i**
Filesystem                     Inodes  IUsed    IFree IUse% Mounted on
udev                          2037022    623  2036399    1% /dev
tmpfs                         2045944    918  2045026    1% /run
/dev/mapper/xubuntu--vg-root 14606336 634125 13972211    5% /
tmpfs                         2045944      1  2045943    1% /dev/shm
tmpfs                         2045944      6  2045938    1% /run/lock
tmpfs                         2045944     18  2045926    1% /sys/fs/cgroup
/dev/sda1                      124928    317   124611    1% /boot
tmpfs                         2045944     29  2045915    1% /run/user/1000
```

---

### Post by westie457 on 2018-12-11
Hhhmmm, not what i was expecting or hoping for and the fact you are using a LVM possibly makes things more complicated.
My knowledge of lvm is next to zero so things I suggest might break something.

Have you ever 'trimmed' your SSD?
This might be of some help. [https://www.howtogeek.com/176978/ubuntu-doesnt-trim-ssds-by-default-why-not-and-how-to-enable-it-yourself/](https://www.howtogeek.com/176978/ubuntu-doesnt-trim-ssds-by-default-why-not-and-how-to-enable-it-yourself/)

---

### Post by stinktier2 on 2018-12-11
> **westie457 said:**
> Hhhmmm, not what i was expecting or hoping for and the fact you are using a LVM possibly makes things more complicated.
My knowledge of lvm is next to zero so things I suggest might break something.

I believe I just used the default options when I installed this system – erase complete disk and install Xubuntu.

> **westie457 said:**
> Have you ever 'trimmed' your SSD?
This might be of some help. [https://www.howtogeek.com/176978/ubuntu-doesnt-trim-ssds-by-default-why-not-and-how-to-enable-it-yourself/](https://www.howtogeek.com/176978/ubuntu-doesnt-trim-ssds-by-default-why-not-and-how-to-enable-it-yourself/)

Not that I know of. The error is pretty new, for months everything worked fine and last week it showed up when I wanted to move some big folders to make some more room. Now even when I try to duplicate (copy/paste) a 2GB folder it crashes the system.

---

