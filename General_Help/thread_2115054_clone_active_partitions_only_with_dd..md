---
title: "clone active partitions only with dd."
date: 2013-02-11
forum: General Help
---

### Post by Ceiber Boy on 2013-02-11
Objective: use dd to clone os (multiple partition OS) from one hardisk to another.

Problem: destination disk smaller than origional disk.

Thus far: shrunk main partition down, so i have two small partitions and one large partition of free space.

Question: how do i now (using dd) clone the two small partitions with the os and boot partition to the new disk, ingnoring the free space from the origional disk so that it fits?

Hope this makes sence, please ask any questions.

Thanks

---

### Post by The Cog on 2013-02-11
You need to create the partitions on the destination disk before you can write contents to them. I would suggest using gparted for this.

You can copy partitions with dd. Let's assume that you want to copy partition 2 of disk sda to partiton 1 of disk sdb. The command would be:
```
sudo dd if=/dev/sda2 of=/dev/sdb1
```


However, I would be inclined to format the destination drive partitons and then use rsync to copy the partition contents. This would remove the requirement for exactly matching the destination partition size before copying.

```
sudo mkdir /mnt/src
sudo mkdir /mnt/dst
sudo mount /dev/sda2 /mnt/src
sudo mount /dev/sdb1 /mnt/dst
sudo rsync /mnt/src/* /mnt/dst/
```

But there is more to transferring the system than that. You need to install a bootloader. I recently found that a bootable CD called systemrescuecd can boot a linux from hard disk even without a bootloader. Remove the disk that you copied from, so the new system is the only linux to befound. Then use systemdescuecd ro find and boot the hard disk linux. After booting, run the commands
```
sudo update grub
sudo grub-install /dev/sda
```
Then hopefully your new disk will be bootable.

---

