---
title: "Disk access denied"
date: 2007-06-18
forum: General Help
---

### Post by technofossil on 2007-06-18
I have just updated to Feisty.

My system has 2 internal drives:
     1 IDE
          hda1 - /
     1 SATA
          sda1 - /media/disk
               Owner = root, Group = root
               all accesses are: list, create/delete/, no access.

When I try to open  /media/disk (in the file browser) I get a message:  "Access to this internal disk it is restricted to system administrators for security reasons."  It then requires root password.

This is the data disk for my system.  When I view the disk contents, none of the files or directories have the correct icons (all show as documents).  I cannot open anything, including .gz, .tar, .ods, .pdf, or folders. 

If I open a terminal and sudo, I can copy files to / and then change the permissions.  When I cp back I still cannot open the files.

The drive is not in fstab.  The properties window lists the mount options as: rw nosuid nodev data=ordered

I created an entry in fstab and the result was the same, the fstab entry was ignored.

What do I do next.

Thanks in advance for all help.

---

### Post by DagMan on 2007-06-18
```
sudo chown $USER:$USER /media/disk -R
 
```
With it unmounted then mounted often helps, however this sounds a little differant with the icons the looking like they are.

---

### Post by technofossil on 2007-06-19
DagMan: 

Thanks for the reply.  When I frost changed ownership, it worked.  Now the problem changes.

During the boot I see the disk check utility verifying the disk.  When I open the file browser, the disk is not there (mounted or unmounted).

When I "mount -a" I get a message that /media/disk does not exist.

Should I start to panic yet??

---

