---
title: "ZFS Raid not showing in Nautilus/GParted"
date: 2016-04-23
forum: General Help
---

### Post by Gridwalker on 2016-04-23
As 16.04 has announced it now has native ZFS support, I thought I would test Raid-Z. I have had a number of issues with MDADM corrupting my superblocks when a drive fails, so I thought trying something new would be a good idea (having just lost 4tb of media).

So far, so good. ZFS pools seem easy to set up and they auto-mount, but I have one minor nagging issue - the ZFS pool mounts as a folder, but does not show up as a drive in nautilus, GParted, Disks, etc. 

The weird thing is that it has OCCASIONALLY (and very briefly) appeared in the Disks app as MD2, and editing the mount options to name the drive will make it show in nautilus, but the disk will be then be inaccessible due to incorrect mount options. I have Webmin installed for managing MDADM partitions, and visiting the file system listing page lists a device of unknown type mounted as RAID device 2 under the correct mount point. I can move files to the mount-point folder, and viewing the folder's properties in Nautilus will show a partition of the correct size.

So, I know the VFS partition is working, but it isn't showing up in the interface as a proper drive. I know it isn't the end of the world, but I'd really like it to show up correctly in the interface. Does anyone have any suggestions how I can rectify this?

---

### Post by QDR06VV9 on 2016-04-23
I have not had a chance to play with the ZFS yet so I am not going to be of much help here but have you had chance to see this yet?
[http://docs.oracle.com/cd/E19253-01/819-5461/6n7ht6r3m/index.html](http://docs.oracle.com/cd/E19253-01/819-5461/6n7ht6r3m/index.html)
That might get you a start until someone that is a little more knowledgeable with the ZFS.
Kind Regards

---

### Post by Gridwalker on 2016-04-23
I've checked it out, but I've not found anything that helps. The problem isn't so much mounting the drive (I am in the middle of transferring over 1tb of data to it now) just that the GUI isn't showing it as a drive, only as a folder in the root file system.

Like I said, it isn't the end of the world ... things like this just bug me.

---

### Post by Gridwalker on 2016-04-23
Interestingly, I was just adding some new media to my plex server and THAT picked up my VFS drive immediately. So it seems that it is just GTK based apps that can't see the VFS pool as a drive, if that helps anyone narrow down the issue.

---

