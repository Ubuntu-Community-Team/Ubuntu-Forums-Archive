---
title: "Should I create a mount point for a removable (USB to SATA) backup hard drive?"
date: 2020-11-05
forum: General Help
---

### Post by 777funk on 2020-11-05
I hadn't done this and am noticing some odd results with my backup locations. It's creating a backup on the external drive (via USB to SATA cable) on:
/media/user/backup/
but it's also creating a local backup that it puts in: 

/media/user/backup/

for some reason. I know it's local because after I remove the drive, it's still accessible.

---

### Post by TheFu on 2020-11-05
If the backup program runs when the USB drive isn't mounted, then it will write the files to whatever partition is there. There are lots of techniques to ensure that backups do not run unless the external disk is mounted.  Some people check for a file that only exists on the external storage. If it does not, then they don't allow backups.

I check if the normal mount location is in the mount table. If it is, then I allow backups to run. If not, my backup script prints an error so I know what the problem is and exits.

If the backups are done using a GUI program, I don't know how to verify this except manually. With scripting, checking these things isn't hard.

---

### Post by ajgreeny on 2020-11-05
I just let my external disk mount automatically to /media/ajgreeny/Backup, Backup being the label of the partition on the external drive.
The partition is formatted to ext4 in order to keep all file permissions the same as the source, and I have changed the ownership of that mountpoint to myself as user with ```
sudo chown -R ajgreeny:ajgreeny /media/ajgreeny/Backup
```
If the ownership is not changed to me as user it will belong to root, so useless as a backup destination, as I would be able to write to it as root only, not as user.

Without the disk attached that mountpoint does not exist so the backup command will fail.

---

### Post by BarnOwl on 2020-11-06
I specifiy my backup partitions in fstab with the noauto option and explicitly mount them when a backup is running then unmount them.  Since I upgraded to 20.04, i"m experiencing a weird problem with one of them automounting that's being discussed in another thread.  That's another issue though.  Personally, I prefer to specify my mountpoints for backup.

---

### Post by TheFu on 2020-11-06
> **BarnOwl said:**
>  Personally, I prefer to specify my mountpoints for backup.

Agreed.  I want to know where backups are stored.  However, I use a backup server, so the backup storage is located on a completely different physical machine from all the others. The backup tool I use (and most of the real backup tools) all support remote backup capabilities over ssh. Most actually use ssh for all network backups by default.

Automatic mounting usually is based on the label of the partition. So if the LABEL is set to Backups, then the mount would be 
**/media/{username}/Backups/**.  For ext4 file systems, this is probably fine.  For NTFS or other file systems, the automatic mounts don't usually include performance enhancing options. I know for NTFS they do not, so the performance is about 30% slower than needed.

---

### Post by BarnOwl on 2020-11-06
> **TheFu said:**
> Agreed.  I want to know where backups are stored.  However, I use a backup server, so the backup storage is located on a completely different physical machine from all the others. The backup tool I use (and most of the really backup tools) all support remote backup capabilities over ssh. Most actually use ssh for all network backups by default.

I've got a different setup for different needs.  What qualifies as my backup server is e multipurpose machine that serves up movies and is a Mythtv backend as well.  So, my backup scheme is a bit muddied.  I actually do backup other machines there but, I also have to perform local backups.  Regardless, I do think you need to have specified mountpoints for your backups and avoid having them automounted in /media.

---

### Post by ajgreeny on 2020-11-06
When I attach the external drive I use for my backups **it always**, and I mean that, **it always**, mounts to the same mountpoint automatically which surely amounts to the same thing as you are saying is necessary, ie, having a specified mountpoint.

I do not have and do not need any complicated backup procedure as I am just using a simple desktop and laptop computer and in both cases the backup drive always mounts to /media/ajgreeny/Backup and is used simply for my personal files and folders; I have no need to backup the OS as it is so quick to reinstall if needed in my situation.

---

### Post by tea for one on 2020-11-06
Yes, I have to concur with [COLOR="#0000FF"]ajgreeny[/COLOR].

My external, removable device is also labelled Backup and it also mounts in exactly the same place.

No excessive management or complications.

---

