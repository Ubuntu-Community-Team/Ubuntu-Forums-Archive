---
title: "MultiBoot - Device Mixups"
date: 2016-06-16
forum: General Help
---

### Post by Krister Hallergard on 2016-06-16
Have a very strange problem. Disk 0 in windows becomes Device sdb in Linux, and Device sda in Linux becomes Disk 1 in Windows. What controls the disk/device order? Motherboard firmware? Grub2 entries? /etc/fstab? [http://goo.gl/TfDrGU](http://goo.gl/TfDrGU)

---

### Post by oldfred on 2016-06-16
BIOS.

But if booting grub on sdb, BIOS/grub will set that drive as hd0. And grub in booting Windows usually has a devicemap setting to switch drive order, so Window can still see itself as hd0.

Also SATA port order is normally default drive order in BIOS/UEFI.
But I have skipped a port in BIOS system and flash drive that was sde when plugged in, became sdb and every other drive(than sda) moved up a letter. I had sda plugged into SATA0, but I had skipped SATA1.
You would think I had learned, but new UEFI system I had SSD on SATA0, DVD on SATA1 and HDD on SATA2. And while Ubuntu saw HDD as sdb, grub/UEFI saw it as hd3, DVD had messed up my order. Once I moved cables around then it was ok.

---

### Post by Krister Hallergard on 2016-06-16
Thanks oldfred!  Confusing isn't it!  I don't mind that Windows Drive 0 becoming sdb on Linux, though I don't think it is logical.  What I do mind is that it is not persistant.  When occasionally it becomes sda it confuses all my shortcuts, and worse the mounts at boot time set up in /etc/fstab blocks the boot completion on some distros.  I have moved cables around now, but I will not know for awhile if this improve things persistantly.

---

### Post by Jason_Hunter on 2016-06-16
That's because you don't reference sda sdb whaterver, you do this in /etc/fstab

UUID=60c339bd-88f8-4d5c-b68d-bcafca3c7dcc /               ext4    errors=remount-ro 0       1
UUID="9227f224-cc08-4ec4-9556-9376161edff1" /mnt/9227f224-cc08-4ec4-9556-9376161edff1 ext3 defaults 0 0
UUID="beeba51b-e5d5-4008-8c77-fc22bd78fbb7" /mnt/beeba51b-e5d5-4008-8c77-fc22bd78fbb7 xfs defaults 0 0
UUID="a213b46e-3245-42cc-b93c-201a7ea0bc08" /mnt/a213b46e-3245-42cc-b93c-201a7ea0bc08 xfs defaults 0 0

You can use the blkid command to get the uuid of the file system.

---

### Post by Krister Hallergard on 2016-06-17
Jason_Hunter thanks!  I think I understand what you are saying.  I do use UUID in /etc/fstab for the distro I am booting but not for mounting other partitions.  If I were to do that as well, it does not matter if it boots as sdb or sda.  Right?  What about the mount points, they don't necessarily have to be the mount point?  Couldn't I for instance use the shorter /mnt/sdb7 (which I already have as a shortcut) - and it would still function even if the boot is sda!? Like this:  UUID="9227f224-cc08-4ec4-9556-9376161edff1" /mnt/sdb7 ext3 defaults 0 0

---

### Post by yancek on 2016-06-17
Yes, you can use /mnt/sdb7 as the mount point as long as you have that entry in the fstab.  No reason to use the UUID under the /media or /mnt directory if you don't want.  That's just the default way used to access external drive partitions and certainly not a requirement.  If you are booting from the same drive always and not changing/adding/removing drives I would not expect the results to change.  Not sure why that would happen.

---

### Post by Krister Hallergard on 2016-06-17
Thank you guys!  That was the solution, not to sdb sometimes becoming sda, but eliminating the bad effects of it.

---

