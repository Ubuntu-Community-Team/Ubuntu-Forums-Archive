---
title: "Ubuntu won't boot!"
date: 2008-02-10
forum: General Help
---

### Post by robinzxp on 2008-02-10
Hi

I have Ubuntu 7.10 and Windows XP installed with grub as bootloader.
Today when I tried to boot up with Ubuntu it suddenly gave "Error 13: Invalid or unsupported executable format". However Windows boot up fine. I'm sure it's something simple that needs to be tweaked to get it working again (I hope!), any ideas?

---

### Post by src2206 on 2008-02-11
Did you use any disc Partitioning utility (or some other way) to change the drive letter of the partition where Ubuntu is installed?

---

### Post by robinzxp on 2008-02-11
I haven't used any partitioning tools at all, it just happened today when I turned my laptop on. I haven't installed anything on both OS for while. (Apart from Ubuntu updates time to time)

---

### Post by Dojan5 on 2008-02-11
You use a laptop, hmm, do you have two harddrives on it?
If not, you must have used a partitioning tool, for as what i know you can't have two OS's on the same Harddrive without partitions.
If you have two harddrives you boot from i would check if both are masters. Some computers have problems with that.

---

### Post by src2206 on 2008-02-11
Can you boot in Windows XP? If yes then do the following:

Right Click on My Computer and select "Manage"
From the left pane, choose Disc Management
Now note down the different partitions you have. It should list the partition with Ubuntu as Unknown but Healthy partition. If you find that, then post here the numerical position of that partition wrt the first partition which should be the "C"

Otherwise you can always reinstall Ubuntu GRUB using the Live CD.

---

### Post by robinzxp on 2008-02-11
> **src2206 said:**
> Did you use any disc Partitioning utility (or some other way) to change the drive letter of the partition where Ubuntu is installed?

I misunderstood you, I thought you meant recently. I used Default partitioning tool given by Ubuntu to sort out my partitions when I installed my operation systems.

I have 3 partitions.
WindowsXP C:
19.53GB NTFS Health (System)
16.94GB Healthy (Unknown Partition)
800MB Healthy (Unknown Partition)

I'm not sure what u mean by "numerical position of that partition", but they're all on one hd

---

### Post by src2206 on 2008-02-11
Using your Live CD, can you post the menu.lst file content here?

---

### Post by robinzxp on 2008-02-11
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d36cf998-f3ba-4166-a1ac-68dbd5a9ed62 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d36cf998-f3ba-4166-a1ac-68dbd5a9ed62 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

---

