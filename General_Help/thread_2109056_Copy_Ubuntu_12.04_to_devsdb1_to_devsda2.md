---
title: "Copy Ubuntu 12.04 to /dev/sdb1 to /dev/sda2"
date: 2013-01-26
forum: General Help
---

### Post by cigtoxdoc on 2013-01-26
I got an unplanned early start on converting XP to Ubuntu when on of my production XP machines suddenly died.  I already had a development machine with Ubuntu 12.04 64-bit in the works, so I just moved out the dead box, conncted up the good one, and added the 256 MB Crucial M4 SSD with the XP files to the new box (all SATA motherboard).  No data was lost as it was all on the SSD and also on kineticd offsite backup.  I have moved all data files from the XP partition on the SSD (/dev/sda1) to the HD with Ubuutu (/dev/sdb1).  I have used gparted to reduce the size of the ntfs file system (/dev/sda1) down to 80 MB and create a 146.48 MB ext4 partition in the free space.  The ext4 partition is /dev/sda2.  Now I want to copy everything (including what makes drive boot Ubuntu) from /dev/sdb1 to the ext4 partition on /dev/sda2.

How should I do this.  I don't want to start with a fresh install of Ubuntu in /dev/sda2 as have spent many hours getting Crossover configured to run essental MS Windows programs.  The HD that is currently /dev/sdb1 goes to the next development PC.

John

---

### Post by oldfred on 2013-01-26
I really recommend clean installs and copy /home as that is user settings & files. But do not know where crossover hides its files.

I hope you meant GB not MB as Ubuntu needs 5GB as a minimum.

If not using old drive then you can copy. Issue is that image copies include UUID and if you have duplicates (old drive & new drive) system gets very confused. 
Often still best to reinstall grub since yoiu are imaging a partition not the drive.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

    
       Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

    
I would suggest rsync and parameters to preserve ownership & permissions. But then new drive has different UUIDs. You would have to reinstall grub and edit fstab with new UUIDs.

       Move entire OS to another drive - but new install often easier
[http://ubuntuforums.org/showthread.php?t=1929671](http://ubuntuforums.org/showthread.php?t=1929671)

I think you can also just use gparted.

---

### Post by cigtoxdoc on 2013-02-04
Clonzilla did the job, perfectly and without any special steps.

John

---

