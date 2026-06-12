---
title: "Partition Advice to Increase Ubuntu Size"
date: 2015-02-28
forum: General Help
---

### Post by tashfeen_ekram on 2015-02-28
I have a dual boot with a dead Windows boot. My Ubuntu size is getting small and need to increase it. I have included a few pcitures from Gpart. If I were to take the "unallocated" space after the Vista and add it to the Vista partition, then take that much from the increased Vista partition and add it to "/dev/sda1" which is where my Ubuntu lives. Also, there is some error it gives me regarding the Vista partition. 

Thanks!

[ATTACH=CONFIG]260342[/ATTACH][ATTACH=CONFIG]260343[/ATTACH]

(Sorry, you can ignore the thumbnail attached below)

---

### Post by oldfred on 2015-03-01
Gparted will not mount a NTFS partition that has issues, usually it needs chkdsk or could have been left hibernated. You should use your Windows repairCD or flash drive and run chkdsk so you can mount the NTFS partition with Linux tools.

Recursive partition is a different issue, post this to see what it says.
sudo fdisk -lu
sudo parted -l

---

### Post by Impavidus on 2015-03-01
If you have to move or resize the Windows partition, best to do so from within Windows. Gparted can damage Windows partitions. So first fix Windows, resize the Windows partition from within Windows and reboot Windows a couple of times to let it finish the operation. Then resize the Ubuntu partition using gparted.

Alternatively, make a fresh start by wiping the drive and reinstalling everything. Make sure you have good backups. Ubuntu may be able to mount the Windows partition read-only.

In fact, make sure you have good backups either way.

---

