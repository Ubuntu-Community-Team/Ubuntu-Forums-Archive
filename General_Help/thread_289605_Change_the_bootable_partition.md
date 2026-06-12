---
title: "Change the bootable partition"
date: 2006-10-31
forum: General Help
---

### Post by DCMir on 2006-10-31
Hi,

I have 2 HDs and I need to remove the one which has the bootable partition. To do this I need to make the other HD bootable but it already has Ubuntu installed and I don`t want to format it and lose my data.

Is it possible to make a partition active (bootable) without formatting it and loosing all the data? If it is, how should I proceed?

Thanks for the help...

---

### Post by jordilin on 2006-10-31
I don't know if I understand, but you can change the order of booting in your BIOS. You can choose which hard drive is to boot first.

---

### Post by DCMir on 2006-10-31
> **jordilin said:**
> I don't know if I understand, but you can change the order of booting in your BIOS. You can choose which hard drive is to boot first.

I don`t understand much about it, but the problem is that I need to have at least one bootable partition in the HD, so Grub can correctly load my Ubuntu. As I don`t have any, I need to set one.

---

### Post by Rui Pais on 2006-10-31
hi,
check if reading [this excellent Howto]("https://help.ubuntu.com/community/GrubHowto") answer you question.

Do you have a /boot partition on the 2nd HD? or the other ubuntu installation uses the same /boot on first HD?

If you have a boot partition on each of your disks you can make them bootable by running
```
sudo fdisk /dev/hdb
``` (or replace hdb by your partition)
press 'p' to see if that partition is already bootable (it will have a * in front of name) if not press 'a' and enter the number of partition.

---

### Post by DCMir on 2006-10-31
> **Rui Pais said:**
> hi,
check if reading [this excellent Howto]("https://help.ubuntu.com/community/GrubHowto") answer you question.

Do you have a /boot partition on the 2nd HD? or the other ubuntu installation uses the same /boot on first HD?

If you have a boot partition on each of your disks you can make them bootable by running
```
sudo fdisk /dev/hdb
``` (or replace hdb by your partition)
press 'p' to see if that partition is already bootable (it will have a * in front of name) if not press 'a' and enter the number of partition.

Thanks for the answer, it is a really great howto. The problem is that I also don`t have a /boot partition. I think there is no way to do what I need without formatting the partition and flag it bootable.

---

### Post by Rui Pais on 2006-10-31
> **DCMir said:**
> Thanks for the answer, it is a really great howto. The problem is that I also don`t have a /boot partition. I think there is no way to do what I need without formatting the partition and flag it bootable.

You would not need to format. 
There is a /boot folder on the ubuntu installation of your 2nd HD? 
if so thats the one you should set as bootable. 
Make a partition bootable did not touch partition data. In fact set a bootable flag is just a precaution. The important part is to set grub on MBR of your 2nd disk and instruct grub install that the /boot is inside the root partition and not on a separated one.

Remove your 1st HD and boot from a liveCD.

Do the steps for install/config grub from the HowTo. 
Its simple, 2 or 3 lines.

If you make any mistake, connect the 1st. HD again and you are back to previous state.

---

### Post by DCMir on 2006-10-31
> **Rui Pais said:**
> You would not need to format. 
There is a /boot folder on the ubuntu installation of your 2nd HD? 
if so thats the one you should set as bootable. 
Make a partition bootable did not touch partition data. In fact set a bootable flag is just a precaution. The important part is to set grub on MBR of your 2nd disk and instruct grub install that the /boot is inside the root partition and not on a separated one.

Remove your 1st HD and boot from a liveCD.

Do the steps for install/config grub from the HowTo. 
Its simple, 2 or 3 lines.

If you make any mistake, connect the 1st. HD again and you are back to previous state.

Thanks Pairs, I didn't know that changing a partition to bootable would not require formatting it. I'll try this as soon as I get home... Can I safely use cfdisk or fdisk for this purpose?

---

### Post by Rui Pais on 2006-10-31
> **DCMir said:**
> Thanks Pairs, I didn't know that changing a partition to bootable would not require formatting it. I'll try this as soon as I get home... Can I safely use cfdisk or fdisk for this purpose?
Yes, of course. 
But the risky part is get grub into the MBR of that disk. If you installed a Linux on it with only that hd connected, thats probabily done it. 
If your linux installation on that disk was done with the other connected, changes are that although you have a /boot on 2nd disk somewhere your grub booter will be on the first (the default for Ubuntu installation, i think).

---

