---
title: "Remove windows 10 from ubuntu dual boot."
date: 2017-05-07
forum: General Help
---

### Post by Hewjr100 on 2017-05-07
Funny thing, I typed the above into google and got the exact opposite. So here I am asking if anyone knows how to remove windows 10 from system that is dual booting with Ubuntu 17.04.

Henry

---

### Post by oldfred on 2017-05-07
It is essentially the same thing.

But HPs are generally not Ubuntu UEFI boot friendly. They violate UEFI specs that say NOT to use description as part of boot. And of course only valid description is "Windows Boot Manager". Several work arounds. Are you using one now?

If only booting Ubuntu you can change the entry in UEFI to boot shimx64.efi to read "Windows Boot Manager". They check description but not actual file used to boot.

I would back up Windows as you paid for it and if later you want to sell system you may need Windows on it. We also see many who find that one app they need that only works in Windows.

        May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

More info in link in my signature below.

You can use efibootmgr to remove entries in UEFI boot menu.
And then remove Microsoft folder in ESP. And then the Windows related partitions.

---

### Post by Hewjr100 on 2017-05-08
Actually my laptop is 4 years old, it uses both uefi and or legacy bios.  Currently using legacy.

Henry

---

### Post by yancek on 2017-05-08
You forgot to post the output of boot repair requested above.  Without more details on your system, all anyone here can do is guess since we don't know which bootloader you are using or what your drive/partitiion structure looks like.  You don't "remove" operating systems in the way you remove application software so the general process would be to simply format your windows partitions which of course, will delete all data on those partitions.  More info needed for specific advice.

---

### Post by ajgreeny on 2017-05-08
If by chance you have already deleted the Windows partition(s) you may simply need to run ```
sudo update-grub
``` to remove its entry from the grub menu.

However, as you have not yet told us anything about your system or what you've done so far we can not help much.  Show us the Boot-info script output as requested above and we have more chance of helping you.

---

### Post by Hewjr100 on 2017-05-08
Well quite simply I did a fresh install of ubuntu. It seemed the best option. I have .mozilla backed up, so setup was easy. Finally decided to get rid of windows.

Henry

---

