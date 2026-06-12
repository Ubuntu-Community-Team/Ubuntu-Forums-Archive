---
title: "WinXP bootloader replaced GRUB"
date: 2006-11-07
forum: General Help
---

### Post by MalcolmCarmen on 2006-11-07
I just formatted my drive (3 primary partitions, one for ubuntu, 2 NTFS for windows + ubuntu/windows) with GParted and installed ubuntu a few hours ago. Shortly after, I installed WinXP, expecting the following issue:

I assume GRUB (minus the prompt) ran out of /boot before I installed XP. Now, only XP will boot up. I'd like to correctly set up XP/ubuntu to dual boot, but I'm not sure how to go about it. I see two ways:

- Try to work with the XP bootloader to get ubuntu to be an option
- Fix (my master boot record?) to make /boot run first again, so I can configure GRUB to boot XP.

I'm using the Ubuntu 6.06LTS install CD to boot up, but I've noticed that GParted has no option to do anything with setting the partition to boot to. Do I need to burn a general utilities distro if I want to go with option #2?

Sorry, I'm not very good at anything partition related, any generalized help that I could take further with google would be appreciated :)

---

### Post by catlett on 2006-11-07
If ubuntu was installed and the issue is XP overwrote grub, this will work.
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by MalcolmCarmen on 2006-11-07
Thanks a lot, that is perfect! :D

---

### Post by trents on 2006-11-07
For future reference, install linux after Windows and you will avoid this problem. Sorry if this sounds obvious. I have made the same mistake as you.

Steve

---

### Post by catlett on 2006-11-07
Now that I think of it, you may need to add an entry for windows. It isn't very difficult but you need to know what partition windows is on. After you get into ubuntu again, enter this
```
sudo fdisk -l
``` That will list your partitions. If windows is your only ntfs partition then it will be easy to figure out which one it is. If not you may have to hunt a bit to discover which partition it is. Anyways post the partition and I'll give you the entry for the grub menu.

---

