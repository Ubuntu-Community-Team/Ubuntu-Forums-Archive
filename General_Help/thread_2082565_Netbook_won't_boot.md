---
title: "Netbook won't boot"
date: 2012-11-09
forum: General Help
---

### Post by Hamoudi on 2012-11-09
Ok, i'll try to make this as short as possible. 
I own a packard bell dot_se 765. Yesterday i've tried installing ubuntu 12.10 on it and i clicked on 
Install it alongside windows 7. After all that it looked fine and dandy until i tried booting windows 7, it wouldn't. Then i tried looking on google how to delete ubuntu and it told me to delete the partition where the ubuntu is on. Well did and now i'm kinda stuck on the boot error: no such partition. Grub rescue thing. 
I've read up a bit about it and it requires me to have a cd of windows, the problem with this is the installation is on the hdd itself and is Accessed by pressing alt+f10 under normal circuimsantces. So now i also can't acces that... But it is still there since when i try to reinstall ubuntu on it again it still asks me to install alongside windows 7 and on the dual boot screen i can asses the recovery system but it tells me that the partition has not enough space on it.

I hope someone can help me out with this.

Thank you in advance,
Hamoudi

Also i wasn't sure if this was the right section for it, but i'm sorry if it's not.

---

### Post by efflandt on 2012-11-10
To restore a normal Windows mbr in place of grub, either boot Ubuntu if you reinstalled it again, or Ubuntu live/install CD or USB (probably whatever you used to install Ubuntu) and if the drive has a regular msdos partition table do:

```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```If you have a GPT partition table you would use gptmbr.bin instead.

If your computer did not include system or recovery disk(s) it probably had a utility for creating one or the other which you should have done before tampering with the drive.  But for a netbook that would typically require an external CD/DVD drive.

---

### Post by Hamoudi on 2012-11-10
> **efflandt said:**
> To restore a normal Windows mbr in place of grub, either boot Ubuntu if you reinstalled it again, or Ubuntu live/install CD or USB (probably whatever you used to install Ubuntu) and if the drive has a regular msdos partition table do:

```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```If you have a GPT partition table you would use gptmbr.bin instead.

If your computer did not include system or recovery disk(s) it probably had a utility for creating one or the other which you should have done before tampering with the drive.  But for a netbook that would typically require an external CD/DVD drive.

Yes, thats correct on my netbook it's by pressing alt+ f10 upon the booting screen, but now i can't acces it by pressing the combination. 
When i install linux alongside windows 7 though one of the options is /dev1 and thats the recovery, but when i go to it it tells me i have insufficient space.

---

