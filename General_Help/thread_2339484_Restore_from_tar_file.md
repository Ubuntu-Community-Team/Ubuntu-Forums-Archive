---
title: "Restore from tar file"
date: 2016-10-09
forum: General Help
---

### Post by BigYellowDog on 2016-10-09
The hard drive on my Ubuntu server has died :(  I have a tar file of the root (/) file system that I am going to use as a restore to a new drive.  I've read the wiki.

IIRC Linux uses a unique drive id, that's stored in /etc/fstab to know how to mount the drives.  There is nothing in the wiki about doing this.  What is the correct syntax.  My fstab has this

> UUID=d4c31218-c9b3-4889-934c-fec5f26788e8 /               ext4    errors=remount-ro 0       1
UUID=990d9cab-339b-4d60-a4bc-84036cdc688a /home           ext4    defaults        0       2
UUID=df9134fd-8430-489b-98b4-6e1fed778349 none            swap    sw              0       0


How do I set the UUID for partition on the new drive.

Also the wiki states using a live CD to install the GRUB loader, I assume I can use my Ubuntu desktop to accomplish this.

---

### Post by TheFu on 2016-10-09
You don't change the UUID on a disk.  You change the fstab. Use **sudoedit /etc/fstab** and **blkid** to get the uuid and edit.

Tar is not a very efficient way to backup anything more than a few hundred MB.  There are better options, if you are interested.

---

### Post by BigYellowDog on 2016-10-09
Oh, I thought I needed to run something like 

> tune2fs -U d4c31218-c9b3-4889-934c-fec5f26788e8 /dev/sdX1

on the new partitions.  Do I also need to update /boot/grub/grub.cfg or does this get built when I run 

> sudo -s
for f in dev dev/pts proc ; do mount --bind /$f /media/whatever/$f ; done
chroot /media/whatever
dpkg-reconfigure grub-pc 

Right now tar is what I have, the gziped tar file is 1.8Gb. I am open to what to use after I rebuild my server.

---

### Post by TheFu on 2016-10-09
[LIST=1]
[*] Install the new disk into the PC.
[*] Attach the backup disk to the PC (assuming it is USB).
[*] Boot off a liveCD/DVD of whatever Linux you like.  Do not install - "try ubuntu" is what you want.
[*] Using **gparted**, create the partitions like your old disk had - be about the same size, but at least as large as the data to be restored. It would be smart to make / and /home separate. However, you probably want to clone the prior install.  For example, if the old install was uefi, then you'll need to restore that stuff too. Hopefully, you backed that up.  Don't forget to create the swap partition.
[*] restore everything using whatever **tar x....** commands you need to push things back where so they appear to be in the correct locations.
[*] Get the new partition UUIDs using **blkid** - sometimes it need sudo, sometimes it doesn't.
[*] Open another terminal and use **sudoedit /etc/fstab** to put the newly discovered UUIDs for each partition into the correct location for the mount
[*] Use **grub-install** and **update-grub** to get booting setup. You'll need to review a different how-to for details. I think a chroot will be necessary with a few **bind mounts** to make things work.
[/LIST]

That should be it. Reboot without the backup disk or optical media connected.

I don't do restores this way and don't use tar for system-level backups. Just too much trouble.  Tar lacks all sorts of things that a modern backup tool has.  The best way for you to do backups depends on your RTO, RPO and how much downtime you are willing to have to perform backups.  I do daily, automatic, versioned backups and downtime can only be a few minutes. That really isn't _downtime_, rather is it time when the services cannot be available - I stop DBs, for example. I do not shutdown the machines.

---

