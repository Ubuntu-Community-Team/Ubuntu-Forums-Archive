---
title: "Boot Reapir Disk wiped mdadm RAID1 data?"
date: 2016-04-19
forum: General Help
---

### Post by toddk63 on 2016-04-19
First, I had a backup, so no panic.  I just would like to know what happened and what could have been done to recover the data

I was experimenting with Boot Repair Disk on my Ubuntu 15.04 server.  I first ran Boot-Info and noted that there was Grub installed on the RAID1 drive as well as the CF/IDE drive that was the bootable OS.  I don't know how it got on the RAID1 drive to begin with. I chose the default repair, not advanced.  Boot repair proceeded to "restore" Grub on all the hard drives in the system (1 RAID1, 2 non-raid, and CF/IDE drive).  After the repair, the RAID1 drive appeared to be empty.  The array was reported as "clean" though.  I ran Boot-Info again and noted that Grub was still only on the RAID1 drive and the CF/IDE drive as before, not on the other 2 non-RAID drives.

Any obvious answers?

Thanks,

Todd K.

---

### Post by oldfred on 2016-04-19
Post links to before & after Boot-Repair reports.

If it really deleted your RAID, then you need to file a bug report with Yann. He at minimum will need those reports and perhaps other data.
[https://bugs.launchpad.net/boot-repair](https://bugs.launchpad.net/boot-repair)

---

### Post by SeijiSensei on 2016-04-20
You can mount the individual component drives of an mdadm RAID1 as ordinary drives.  You might give that a try. Unmount the array if it is mounted, then stop the array ("sudo mdadm --stop").  Now see if you can mount one of the drives like this:
```
sudo mount -t ext4 /dev/sdc1 /mnt
```
assuming the array consists of partitions /dev/sdc1 and /dev/sdd1.  Can you see the files under /mnt?

---

