---
title: "RAID 1 on existing 7.10 install"
date: 2007-10-31
forum: General Help
---

### Post by ogifell on 2007-10-31
Hey all,
 
Im looking to add a small RAID 1 setup to an existing 7.10 install.  It will consist of 2x160G ATA (old i know) hard drives.  I have a Rosewill card available, but I assume it's best to use software RAID.  I would like, in addition to the RAID setup, some sort of GUI, with which I can monitor the status of the array.

If I can get this working, I'm going to make a larger, SATA RAID array, so if anyone can give me some insight, it would be greatly appreciated!

---

### Post by fjgaude on 2007-10-31
Here's the best I can do. See:

[HTML]http://ubuntuforums.org/showthread.php?t=598615&highlight=raid[/HTML]

Hope this helps.

---

### Post by blueorder on 2007-10-31
I used mdadm to setup a software RAID1 array after installing 7.04 server on a separate system drive.

I cannot find the exact HowTo I used but there are not many steps.

Install the new drives, boot into Ubuntu, install mdadm, create identical partitions on each drive, call the mdadm command to create the raid1 array.

EDIT: I found this forum post that had the steps I used. Make note of the step (not explained that much) of when creating the partition on each drive to make them id Linux Raid (can't remember exact wording).

[Link]("http://nixcraft.com/getting-started-tutorials/432-setting-up-raid-1-mirroring-running-remote-linux-system.html")

---

