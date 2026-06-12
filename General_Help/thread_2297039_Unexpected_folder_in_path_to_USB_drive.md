---
title: "Unexpected folder in path to USB drive"
date: 2015-09-30
forum: General Help
---

### Post by Ralph L on 2015-09-30
I am running Xubuntu 14.04.  I have Access Control Lists (ACLs) and Extended Attributes enabled on my OS disk partition, my Shared_Data disk partition (both on my laptop internal disk).   I have a usb disk that has several partitions that I use for backup and other purposes.  All these usb disk partitions also have ACLs and EAs enabled.  In Thunar when I plug in my usb drive, and click on my backup partition to mount it, thunar creates a folder in /media called ralph (my user name), and mounts the usb disk partition as /media/ralph/backup_ext4 (backup_ext4 is the name of the disk partition).  Folder /media/ralph has a named ACL user of "ralph" (I don't know why the system does that).  /media/ralph/backup_ext4 does not have any named ACL users or groups.  If I unmount/eject the usb disk, the folder /media/ralph remains.  If I delete it, it comes back whenever, I plug in the usb drive.
The reason I am concerned about the added folder "ralph" is that I have a number of scripts that I use across multiple ubuntu/ xubuntu/ kubuntu systems (some very old) and none of them inserted the folder "ralph" in the path to the disk drive.  Hence, I need to alter those scripts for use with xubuntu 14.04.

Would someone explain to me why the folder "ralph" is suddenly being added in the path to usb drives??  Also, why is that folder being given a named ACL user entry of "ralph".  I don't see the need for either!!  Is the folder "ralph", with its named ACL entry, there just because I have enabled ACLs??   Is it something that has a purpose and for which I should go to the trouble of rewriting my scripts, or is it something that will soon "go away", because it is unnecessary??  I think I can force non-use of the folder "ralph" by putting entries for my usb drive in /etc/fstab (although I haven't tried that yet) but will I mess something else up.

Any help is appreciated..........
 .

---

### Post by Dennis N on 2015-09-30
USB drives used to be mounted by udisks service at subfolder of /media, like /media/data. Now, Ubuntu uses the newer udisks2 (since Ubuntu 12.10) which mounts such devices at subfolder of /media/<user>, like media/ralph/data. There is no simple user option to change this that I know of.

---

### Post by Ralph L on 2015-10-04
Dennis N,
Thanks for the response.  I did not know about udisks2.  I still don't understand the rationale for what was done, but I will learn to live with it.  Temporarily anyway I did get my scripts to work by putting a symbolic link in /media that points to my usb disk partition (/media/backup_ext4) so that my scripts can "skip around the "ralph" folder that udisk2 put in /media.  It even survived a reboot so maybe it is a long term solution.

---

