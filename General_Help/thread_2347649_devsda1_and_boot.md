---
title: "/dev/sda1 and /boot"
date: 2016-12-27
forum: General Help
---

### Post by David_Partridge on 2016-12-27
When I initially installed this server it was with 14.04 LTS Server.  At that time it had a /boot partition on /dev/sda1 and / and /home on an LVM partition on the same drive.

Along the way I've upgraded to 16.04 and added an Adaptec Raid controller.   During that time I did notice that the SAS RAID array on the Adaptec controller would be at /dev/sda with one kernel and the next week it would be back at /dev/sdb???

Anyway I was doing some work on the system the other day and noticed that the /dev/sda1 partition wasn't mounted as /boot.  When I mounted it temporarily it only had 14.04 kernels on it. The /boot directory in / seems now to contain all the kernels etc.

1) Is this intended?
2) If not what should I do to correct it?
3) If yes what should I do with the /dev/sda1 partition?

Here's my current fstab

```

# <file system> <mount point>         <type>   <options>                    <dump>  <pass>
/dev/mapper/Charon--vg-root /          btrfs   defaults,subvol=@             0       1
/dev/mapper/Charon--vg-root /home      btrfs   defaults,subvol=@home         0       2
/dev/mapper/Charon--vg-swap_1 none     swap    sw                            0       0
#
UUID=cf914647-a613-4ced-b3d8-cda423c48ac5 /shared btrfs    defaults,subvol=@    0       1

```

Thanks
Dave

---

### Post by SeijiSensei on 2016-12-27
Run "sudo blkid" to get a list of the UUIDs for each filesystem.  Then use the "UUID=" method in /etc/fstab rather than /dev/sdX.  This guarantees that the same filesystem will be mounted to the same location each time.

I will say I haven't used LVM for a very long time now.  With the large disk drives commonly available today there is little reason for LVM unless you need to take "snapshots" of the filesystems or have encrypted filesystems.  I don't care about either of those, so I just have ordinary partitions.

---

### Post by David_Partridge on 2016-12-28
That wasn't the problem.  Given the nature of the fstab, all the partitions listed there mounted OK.

The question is about the /boot partition

Thanks, Dave

---

### Post by SeijiSensei on 2016-12-28
Sorry I misunderstood.

If the boot partition stands outside of the root filesystem, it has to be mounted by an entry in /etc/fstab.  Otherwise Ubuntu will not be aware of its existence and place everything in the /boot directory on the main filesystem.  You'll probably need to reconfigure grub to use the kernels in /dev/sda1.  In the past there was a utility called grub-config that handled that task, but on 16.04 it appears the "grubby" application manages boots.  I've never used that but you can take a look at its [manual page]("https://linux.die.net/man/8/grubby") or perhaps some other documentation online.

---

### Post by oldfred on 2016-12-28
If you re-installed with Something Else, then you have to also mount the /boot partition on the partitioning screen, otherwise it is not used & /boot default is inside / (root).

You can with some effort copy all new boot files from boot folder to boot partition, edit fstab to mount /boot partition. 
I would make sure I can boot repair/live install Ubuntu just in case I need to fix something.

---

