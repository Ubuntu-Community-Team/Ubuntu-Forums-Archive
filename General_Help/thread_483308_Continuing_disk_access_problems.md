---
title: "Continuing disk access problems"
date: 2007-06-24
forum: General Help
---

### Post by technofossil on 2007-06-24
Last week I posted:

[INDENT]I have just updated to Feisty.

My system has 2 internal drives:
1 IDE        hda1 - /
1 SATA     sda1 - /media/disk
Owner = root, Group = root
all accesses are: list, create/delete/, no access.

When I try to open /media/disk (in the file browser) I get a message: "Access to this internal disk it is restricted to system administrators for security reasons." It then requires root password.

This is the data disk for my system. When I view the disk contents, none of the files or directories have the correct icons (all show as documents). I cannot open anything, including .gz, .tar, .ods, .pdf, or folders.

If I open a terminal and sudo, I can copy files to / and then change the permissions. When I cp back I still cannot open the files.

The drive is not in fstab. The properties window lists the mount options as: rw nosuid nodev data=ordered

I created an entry in fstab and the result was the same, the fstab entry was ignored.

What do I do next.
[/INDENT]

DagMan suggested **sudo chown /media/disk $USER:$USER -R** 

I tried to chmod -v 666 *.ods (some of the docs on the disk).  I saw the changes were made but I am still not able to access the files. 

ls -l yields:
[INDENT]?--------- ? ? ? ?                ? /media/disk/Auto_Expenses1.ods
?--------- ? ? ? ?                ? /media/disk/Auto Expenses.ods
?--------- ? ? ? ?                ? /media/disk/Auto_Expenses.ods
[/INDENT]

Something is very screwy on this disk.  Any suggestions?  

I just deleted the partition using GParted and re-installed the partition and formatted the disk.  When I tried to create the new partition, I got the message "Access to this internal disk it is restricted to system administrators for security reasons."  It looks like the issue is being create in the lower levels of the OS.

Thanks in advance for all help.

---

