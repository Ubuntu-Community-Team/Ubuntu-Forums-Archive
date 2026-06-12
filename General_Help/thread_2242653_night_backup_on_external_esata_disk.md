---
title: "night backup on external esata disk"
date: 2014-09-03
forum: General Help
---

### Post by atrac2 on 2014-09-03
I need to set a cron job every night that checks if the my esata disk is mounted, if not mounted then mounts it, and backups my home with rsync.
Now, the problem is that esata disks, unlike usb disks, are not mounted automatically: in nautilus I see the disk icon, I click on it and it is mounted on /media/username/LABEL where "username" is my user name obviously and LABEL is the disk label. 
If I try to make a script that mounts the disk the problem is that the /media/username/LABEL directory does not exist (I guess is created by autofs?) and therefore I need to create a separate mount point. But I want the script to work even if the disk is already mounted, and if it is mounted I do not want the script to unmount it since the disk might be busy.
What do you suggest? Maybe create the /media/username/LABEL and put it in fstab? Will it work? What if I have other devices plugged, will the disk be always the same device, for example /dev/sdb?
Thanks

---

### Post by mcduck on 2014-09-03
Plenty of options here. Is the disk going to be always (or at least usually ) connected to the system? In that case using fstab instead of automatic mounting makes sense. And it makes no difference at all what device name the drive is recognised with (indeed, that can change based on other devices connected to the system, and the order in which they are detected during boot). The trick here is that you shouldn't use the device name to mount anything in fstab, instead use the UUID or label of the filesystem and it will always point to the correct drive.

On the other hand, if the disk isn't always connected and you prefer to sue the automatic mounting, you could check if the mount point exists before (or instead of) checking if the drive is mounted and doing anything else. Assuming you have set a label for the drive, the mount point will always have the same name so checking it is easy.

---

### Post by atrac2 on 2014-09-03
> **mcduck said:**
> Plenty of options here. Is the disk going to be always (or at least usually ) connected to the system? In that case using fstab instead of automatic mounting makes sense. And it makes no difference at all what device name the drive is recognised with (indeed, that can change based on other devices connected to the system, and the order in which they are detected during boot). The trick here is that you shouldn't use the device name to mount anything in fstab, instead use the UUID or label of the filesystem and it will always point to the correct drive.

Thanks for your answer. This is clear and I know how to do it.
> **mcduck said:**
> 
On the other hand, if the disk isn't always connected and you prefer to sue the automatic mounting, you could check if the mount point exists before (or instead of) checking if the drive is mounted and doing anything else. Assuming you have set a label for the drive, the mount point will always have the same name so checking it is easy.
If I choose this option, how do avoid using device name? Is there a way to mount the disk with UUID even if not in fstab? And, suppose the cron job creates the LABEL direcory: will the automount delete it if I umount the disk from Nautilus?

---

### Post by sudodus on 2014-09-03
If you use a good descriptive label, and use it to identify the partition, it will be easy and straightforward, in a way similar to using the UUID, so it is *not* using the device name.

I don't think the cron job is supposed to create the label. You create it once, and it will be used until the disk is worn out. The cron job could check if the partition is mounted, and if not, try to mount it (success if connected and power on, otherwise failure).

I would put an entry in the configuration file /etc/fstab, but I would not automount it. I have a similar configuration for my backup drives.

First you must create the mount points, in this case

```
sudo mkdir -p /mnt/E1
sudo mkdir -p /mnt/E2
```

```

# eSATA disk E1 (not always /dev/sdb1)
UUID=5ece9189-9a67-4076-a7ae-382891f4e3f6  /mnt/E1    ext4    defaults,[COLOR=#0000cd]noauto[/COLOR] 0       0
# eSATA disk E2 (not always /dev/sdb1)
UUID=cbfc3a24-ee5d-4840-9fbb-9f07d1cdda9d  /mnt/E2    ext4    defaults,[COLOR=#0000cd]noauto[/COLOR] 0       0

```

Notice the mount option [COLOR=#0000cd]**noauto**[/COLOR], which means it does not automount, and it does not expect the drive to be always connected. So you must mount it before backup, maybe manually, maybe in the backup script. Now (after reboot), /mnt/E1 is enough to define the mount operation, so

```
sudo mount /mnt/E1
```

will mount the partition described by the corresponding UUID. And you unmount it with

```
sudo umount /mnt/E1
```

You can also add the corresponding labels, but it is not necessary. The easiest way to add a label is to use ***gparted***, but you can also do it with the command line tool ***tune2fs*** (for ext file systems). I simply use the labels E1 and E2, which makes the partitions easy to see in file browsers and other tools.

---

### Post by mcduck on 2014-09-03
Yeah, the *mount* command can use label or UUID instead of device name. See the *-L* and *-U* options in *mount*'s manual page.
(also there's */dev/disks/by-uuid/* and */dev/disks/by-label/*, I've never tried but I assume those should work as well)

As far as I know automount shouldn't delete the mount point if it didn't create it in the first place. Either way that shouldn't be a problem, you'll just need to make sure your cron job is checking for all possible situations if you are going to have many different mechanisms mounting & unmounting the drive. Should be pretty simple anyway.

---

### Post by JKyleOKC on 2014-09-03
> **atrac2 said:**
> What do you suggest? Maybe create the **/media/username/LABEL** and put it in fstab? Will it work? What if I have other devices plugged, will the disk be always the same device, for example /dev/sdb?
ThanksThere's a fairly important point here that seems to have slipped by everyone. Look at the suggestion from **sudodus**:> sudo mkdir -p /mnt/E1Notice the difference? You suggest "/media" and he suggests "/mnt" as the basic directory for the mount point. And that difference involves the important point.

Anything mounted in "/media" automagically gets shown in the Nautilus pane; things mounted in "/mnt" do not. This automatic action applies to other actions as well but I don't know the complete list.

For your specific situation, using "/mnt" would seem to be preferable; this would leave your cron job and/or associated script in full control of things with no possibility of automatic actions getting in the way and confusing matters.

---

