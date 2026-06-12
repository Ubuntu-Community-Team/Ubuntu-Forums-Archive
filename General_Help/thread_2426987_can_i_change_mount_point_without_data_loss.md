---
title: "can i change mount point without data loss ?"
date: 2019-09-16
forum: General Help
---

### Post by berry566 on 2019-09-16
Hi, 
i am new to linux, i have a question: can i change disk's mount point, without data loss ?

---

### Post by deadflowr on 2019-09-16
Depends.
Explain what mount point needs to change.

---

### Post by Skaperen on 2019-09-16
if it is just temporarily mounted, like a plug-in device, just unmount it and then mount it where you want it to be.  there must be no open files there to be able to unmount it.

if it is permanently mounted (e.g. always there when you boot up) you cat do this by changing file [COLOR=#0000cd][FONT=courier new]/etc/fstabs[/FONT][/COLOR] but doing this can break many things.  if you want to move the main disk that is mounted at / then explain what you want to accomplish since that cannot be done.

---

### Post by berry567 on 2019-09-16
I have datadisk, it is not system disk. I suspect mount point got changed, since i have dual boot with windows. I need to change it to one mount point i want like sdd2. But i am unsure when i do that, if it wouldn't cause data loss. I need to be 100% sure.

---

### Post by TheFu on 2019-09-16
It depends.  

But disks aren't what OSes care about.   OSes mount partitions or logical volumes, not "disks", so it could lead to massive data loss of the disk was part of a volume group that was used for logical volumes.   BTRFS, ZFS, and LVM can make things much more complicated.

We can't tell from the question asked.  Best to be 100% certain, right?

If you can connect everything up and run a few commands, it should be very clear, quickly, if you'll have issues.
```
df -hT -x squashfs -x tmpfs -x devtmpfs
lsblk
sudo fdisk -l

```
Please post using _code tags_, like I have, so the columns line up.

---

### Post by SeijiSensei on 2019-09-17
In general, the answer is yes, assuming you unmount the device cleanly with "sudo umount /dev/xxx".

To insure that disks get mounted to the same locations each time, you can use UUIDs.  Each device or partition has a unique UUID. You can see them by running the command "sudo blkid".  In /etc/fstab, use the syntax:
```
UUID=8be7c7b3-5d34-4ce2-95f1-5e86de1ebc79   /home     ext4    defaults 0 0
```
instead of /dev/xxx at the beginning of the line.

---

