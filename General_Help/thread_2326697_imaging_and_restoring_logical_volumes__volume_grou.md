---
title: "imaging and restoring logical volumes / volume groups / partitions"
date: 2016-06-03
forum: General Help
---

### Post by jub2 on 2016-06-03
For a GPT partitioned disk with LVM, what are the options for backing up a logical volume or volume group? Coming from Windows, I'm used to apps like Norton Ghost and Acronis TrueImage for imaging and restoring entire partitions.

I've heard of CloneZilla, but it doesn't recognize LVM volumes.

Setup is one disk, with 2 GPT partitions.
#1: small bios_grub partition - /dev/sda1. Partition type EF02.
#2: large partition comprising most of the disk. Partition type 8E00 - LVM. This partition is a physical volume - /dev/sda2, assigned to a volume group. This volume group has /, /home and /swap logical volumes.

I completed a fresh install after overcoming a number of errors, so I'd like to image / (root) and the small grub partition #1, so that I can get back to this state if necessary, without having to go through the install process again.

---

### Post by TheFu on 2016-06-03
If you do imaging, the bits are the bits. It doesn´t matter whether they are *recognized* or not. Just be certain to restore to disks of the exact same geometry.  This applies to whole device backups or you can do partition-based backups as images.

I stopped doing image-based backups after switching to Linux. I consider them to be extremely wasteful on storage AND backup time. Capture the LVM config info:
[LIST]
[*]lsblk
[*]lvs
[*]vgs
[*]pvs
[/LIST]
But it would be easier to just keep the creation cmds as scripts and have those available. Then treat the LVs just like any other partition-based backup.  I use **rdiff-backup**.  Keep 60 or 120 days of versioned backups depending on the risks involved with the system.  For most of the systems here, daily backups take 2-4 minutes. Of course, some take longer - 45+ min due to the amount of daily change data.  rdiff-backup is really efficient.

If you want an image-like backup, boot off alternate media, then import the LVM stuff manually and create the LV backup just like it was a partition.  **fsarchive** is an option.  You can use clonezilla to backup at the partition level. That will get the LVM and all data inside.

Or use the fantastic LVM snapshot facilities to get the data and forget about imaging. Just save the LVM setup stuff with the backups in a way that can quickly recreate the PE/VG/LV setup on new HW. Should be a 3 minute task - worse case. Actually, that stuff is a 20 second task, when scripted.

Of course, if the servers aren´t all snowflakes, using a DevOps tool like ansible, salt, puppet, chef, rexify would be a good method to automate the system build ... along with Cobbler.

Hope this was helpful.  The switch from MSFT-thinking to Unix-thinking isn´t always easy.  Software doesn´t need to be in specific locations, they simply need appear to be in the same location - however that needs to happen. Could be symbolic links or hard links or creative mounts or some other method. Being back on similar storage isn´t really important.

---

### Post by jub2 on 2016-06-03
Thanks. To be honest, a lot of that is over my head. I'll have to read up on rdiff-backup and fsarchive.

For the moment, I just want to have a surefire method of returning to the system as it existed immediately after install and first restart.

So what I've done is:
```

lvcreate --size 10G -n lvrootbkp vg1 (create volume to store backups)
mkfs.ext4 /dev/vg1/lvrootbkp (create filesystem on this volume)
mkdir /mnt/rootbackup (make dir to mount volume to)
mount /dev/vg1/lvrootbkp /mnt/rootbackup (mount)
lvcreate --size 5G -s -n lvsnapshot /dev/vg1/lvroot (create snapshot volume of root)
dd if=/dev/vg1/lvsnapshot of=/mnt/rootbackup/root01.dd  status=progress (image root as it existed at time of snapshot creation)

```

So what I think this accomplishes is an image backup of the root (logical) volume, which I can restore in the event I screw something up as I set up this installation (which I am bound to do). And I'll take snapshots along the way so that I don't have to go very far back in time to undo a screwup.

You're right in that coming from Windows to Linux is forcing me to reconceptualize things. In the Windows world, you can't simply back up files to restore the Windows partition to an earlier state, which is why something like the differential backup you referenced makes no sense to me! I'll have to read some more.

---

### Post by TheFu on 2016-06-04
Probably want to mount the snapshot read-only.
[http://www.tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](http://www.tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html)

If an image backup were the goal, I´d just use dd on /dev/sda.

---

