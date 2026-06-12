---
title: "Can't get easybcd working"
date: 2008-05-06
forum: General Help
---

### Post by ilovelinux33467 on 2008-05-06
I have installed Windows XP and Windows Vista as a dual boot. I installed EasyBCD under Vista to try and triple boot with Ubuntu, Vista and XP. My operating system drive has 1 Primary partition (XP), 1 Extended Partition which has 3 logical partitions in it (Vista, Linux EXT3, Linux Swap). When I ran the Ubuntu Install I manually partitioned my hard drive. The Linux EXT3 logical partition was /dev/sdd6 and the Linux Swap Partition is /dev/sdd7. When it comes to the part where it has the Advanced button to configure the boot loader. When I click on it I type in /dev/sdd6 to install it to the first sector of the partition. I installed Ubuntu. It asked me to reboot my computer so I did once it had installed. Vista started up fine so I went into EasyBCD to add ubuntu. I selected the EXT3 partition. I rebooted my computer and ubuntu showed up in the boot loader! I tried to boot into it but all I got was a blinking cursor! :( Can someone help me on this??? Thank you

---

### Post by ilovelinux33467 on 2008-05-06
bump

---

### Post by ilovelinux33467 on 2008-05-06
Please Anyone??? I'm really desperate here

---

### Post by mc4man on 2008-05-07
> The Linux EXT3 logical partition was /dev/sdd6 and the Linux Swap Partition is /dev/sdd7. When it comes to the part where it has the Advanced button to configure the boot loader. When I click on it I type in /dev/sdd6 to install it to the first sector of the partition
Are you sure that shouldn't be sda6, 7 ? (typo ?)

---

### Post by ilovelinux33467 on 2008-05-07
No I have four hard drives in my computer and Ubuntu says it is drive SDD

---

