---
title: "Problems with booting of the Windows"
date: 2007-04-18
forum: General Help
---

### Post by RedMaster on 2007-04-18
Hi!
Amm... I have a problem when i try to boot the windows... I have Ubuntu 6.06 and Windows XP and im using GRUB for boot loader...

Here is the menu.lst :
```
title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda7 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```


When I try to boot the windows it cant... nothing happend and the windows dont boot :| 

Thank you a lot! :)

---

### Post by FRuMMaGe on 2007-04-18
By "nothing" do you mean a black screen?

If so, try leaving it for 5 minutes and it may boot up.  Thats what mine does for some reason.

---

### Post by John.Michael.Kane on 2007-04-18
More info is needed.

Did windows boot fine before?

Are there any errors messages displayed?

Have you ran any updates on your ubuntu install eg: kernel updates ect.?

---

### Post by RedMaster on 2007-04-18
Windows was perfect before when i installed the Ubuntu... It dont show my any errors and maybe if i wait some minutes will boot :| I was waiting 1-2mins... Ok, i will try again and i will tell you back. Thank you! :)

---

### Post by RedMaster on 2007-04-18
No, it didnt boot again. But i noticed something. It displaying that: "Filesystem type unknow, partition type 0x7"

Here is some info:
I have 1 SATA hard - 1 NTFS partition (Windows XP), 1 ext3 (Linux) and 1 FAT32... The NTFS partition is 10GB.

Can be NTFS filesystem the problem and for that GRUB it cant boot the OS?

---

### Post by RedMaster on 2007-04-18
any suggestions about how to boot the stupid Windows? :|

---

### Post by silverglade00 on 2007-04-18
Can you see your XP files in Ubuntu? It sounds like either GRUB lost track of your XP partition or your XP partition got corrupted. If you can see your files ok in Ubuntu, back up the important stuff right away and then try to reinstall GRUB. Partition type 0x7 is NTFS, so there could be corruption that causes GRUB to see it as unformatted.

---

### Post by RedMaster on 2007-04-18
> **silverglade00 said:**
> Can you see your XP files in Ubuntu? It sounds like either GRUB lost track of your XP partition or your XP partition got corrupted. If you can see your files ok in Ubuntu, back up the important stuff right away and then try to reinstall GRUB. Partition type 0x7 is NTFS, so there could be corruption that causes GRUB to see it as unformatted.

Yep, i can see the NTFS partition under Ubuntu... 
Can you help me with the reistalling the GRUB, because im afraid that maybe something will gone wrong and i will have need to reinstall ubuntu :|

I dont have floopy and i cant make rescue disk :|

Thank you!!!

---

### Post by RedMaster on 2007-04-19
Will somebody help me?! :) 

I dont know how to spend this problem :| Somebodt told me to reinstall the GRUB, but I havent got floppy and I cant make a bootable disk if something going wrong... Can you tell me how to reinstall the GRUB without something going wrong :) 

My Linux is Ubuntu 6.06 

Or can you tell me if there are other way to boot the Windows without GRUB? The linux and the windows are on the same hard disk 
Thank you!

---

