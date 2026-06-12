---
title: "LVM and fsck help"
date: 2008-04-17
forum: General Help
---

### Post by modnar0741 on 2008-04-17
I'm running LVM on my system to make many hard drives appear as one.  It appeared that one of the hard drives crashed.  I kept getting a "file system is read only" error even though all permissions were correct.  I made the mistake of running fsck which produced the following (many lines removed which were duplicates of the same problem on different files):
```

root@tehsrvr:/home# fsck /dev/vg/samba 
fsck 1.40-WIP (14-Nov-2006)
fsck.jfs version 1.1.11, 05-Jun-2006
processing started: 4/16/2008 22.47.25
Using default parameter: -p
The current device is:  /dev/vg/samba
Block size in bytes:  4096
Filesystem size in blocks:  377914368
**Phase 0 - Replay Journal Log
**Phase 1 - Check Blocks, Files/Directories, and  Directory Entries
**Phase 2 - Count links
Incorrect link counts have been detected. Will correct.
**Phase 3 - Duplicate Block Rescan and Directory Connectedness
Directory entries for unallocated files have been detected.  Will remove.
**Phase 4 - Report Problems
File system object DF76 is linked as: /lost+found
Errors detected in Directory Index Table. Will Fix.
File system object FF348227 is linked as: /movies/cats/milo.avi
cannot repair the data format error(s) in this file.
cannot repair FF348227.  Will release.
File system object FF348285 is linked as: /linux/ubuntu-7.04-desktop-amd64.iso.md5
The path(s) refer to an unallocated file. Will remove.
File system object DF495644 is linked as: /public/Subs
File system object FF503823 is linked as: /lost+found/D495616.RCN/2002/Trial 20020901.avi
File claims cross linked block(s).
cannot repair FF503823.  Will release.
File system object FF507938 is linked as: /lost+found/D495616.RCN/2003/Trial 20030130.avi
cannot repair the data format error(s) in this file.
cannot repair FF507938.  Will release.
File system object DF704518 is linked as: /projects
File system object DF716878 is linked as: /public/ted
File system object DF749583 is linked as: /linux
File system object DF793107 is linked as: /projects/graph-CUDA/obj/release
**Phase 5 - Check Connectivity
**Phase 6 - Perform Approved Corrections
42 files reconnected to /lost+found/.
**Phase 7 - Rebuild File/Directory Allocation Maps
**Phase 8 - Rebuild Disk Allocation Maps
1511657472 kilobytes total disk space.
    39843 kilobytes in 11879 directories.
1403460303 kilobytes in 63007 user files.
        4 kilobytes in extended attributes
   808044 kilobytes reserved for system use.
107428964 kilobytes are available for use.
Filesystem is clean.
root@tehsrvr:/home# 

```

So two questions:
1) Is there an LVM command which will tell me which of the 5 hard drives is the problem?
2) Assuming I can get the problem HD working long enough to migrate the data off ([http://tldp.org/HOWTO/LVM-HOWTO/removeadisk.html](http://tldp.org/HOWTO/LVM-HOWTO/removeadisk.html)), is there a way to undo the damage that fsck did?

Thanks,
Sean

---

### Post by modnar0741 on 2008-04-17
bump.i

---

### Post by handband2 on 2008-04-17
Here is a list of commands:
[LIST]
[*]**fdisk**
[*]**pvcreate:** create new physical volume.
[*]**pvscan:** list all physical volumes in system.
[*]**vgdisplay:** display volume group information.
[*]**vgextend:** add physical volume to a volume group.
[*]**vgscan:** list all volume groups in the system.
[*]**mkfs.ext3:** making filesystem (formatting).
[*]**mount** and **umount**
[*]**lvextend:** extend the size of a logical volumes.
[*]**lvscan:** locate all logical volumes in the system.
[*]**resize2fs:** resizing a file system.
[/LIST]

Good site for information on LVM:  [http://blog.fuhan.net/linux-easy-step-by-step-logical-volume-manager-lvm.html](http://blog.fuhan.net/linux-easy-step-by-step-logical-volume-manager-lvm.html)

To fix a damaged disk I would recommend [Spinrite]("http://www.grc.com/spinrite.htm").  It does cost but it works great.

---

### Post by mick8985 on 2008-04-17
When you joined the hard drives as one did you just do ```
mkfs.ext3 /dev/vg/samba
```, or did you format them all as ext3 before you added them to the volume group?

---

### Post by modnar0741 on 2008-04-17
I formatted them all as one.  The LVM way.

---

### Post by modnar0741 on 2008-04-17
> **handband2 said:**
> Here is a list of commands:
[LIST]
[*]**fdisk**
[*]**pvcreate:** create new physical volume.
[*]**pvscan:** list all physical volumes in system.
[*]**vgdisplay:** display volume group information.
[*]**vgextend:** add physical volume to a volume group.
[*]**vgscan:** list all volume groups in the system.
[*]**mkfs.ext3:** making filesystem (formatting).
[*]**mount** and **umount**
[*]**lvextend:** extend the size of a logical volumes.
[*]**lvscan:** locate all logical volumes in the system.
[*]**resize2fs:** resizing a file system.
[/LIST]

Good site for information on LVM:  [http://blog.fuhan.net/linux-easy-step-by-step-logical-volume-manager-lvm.html](http://blog.fuhan.net/linux-easy-step-by-step-logical-volume-manager-lvm.html)

To fix a damaged disk I would recommend [Spinrite]("http://www.grc.com/spinrite.htm").  It does cost but it works great.

That's a great list for people who want to get started using LVM.  Unfortunately I've already gotten started and now I'm trying to fix an error.  Any help with those two questions?

---

### Post by handband2 on 2008-04-17
The commands help diagnose the problems which occur.  I use the site to keep my LVM's running.

What is the output for:
```
# pvscan
```

What is the output for:
```
# lvscan
```

What is the output for:
```
# vgscan
```

---

### Post by modnar0741 on 2008-04-17
```

root@tehsrvr:/home/samba# pvscan 
  PV /dev/mapper/sdb1   VG vg   lvm2 [233.75 GB / 0    free]
  PV /dev/mapper/sdd1   VG vg   lvm2 [233.75 GB / 0    free]
  PV /dev/mapper/sde1   VG vg   lvm2 [279.46 GB / 0    free]
  PV /dev/mapper/sdc2   VG vg   lvm2 [465.66 GB / 0    free]
  PV /dev/mapper/sda1   VG vg   lvm2 [279.46 GB / 29.46 GB free]
  Total: 5 [1.46 TB] / in use: 5 [1.46 TB] / in no VG: 0 [0   ]
root@tehsrvr:/home/samba# lvscan 
  ACTIVE            '/dev/vg/usr' [4.00 GB] inherit
  ACTIVE            '/dev/vg/home' [512.00 MB] inherit
  ACTIVE            '/dev/vg/opt' [512.00 MB] inherit
  ACTIVE            '/dev/vg/var' [5.00 GB] inherit
  ACTIVE            '/dev/vg/tmp' [512.00 MB] inherit
  ACTIVE            '/dev/vg/samba' [1.41 TB] inherit
  ACTIVE            '/dev/vg/swap' [512.00 MB] inherit
  ACTIVE            '/dev/vg/NewOS' [10.00 GB] inherit
root@tehsrvr:/home/samba# vgscan 
  Reading all physical volumes.  This may take a while...
  Found volume group "vg" using metadata type lvm2

```

Most of the logical volumes listed are from another operating system and aren't actually mounted.  NewOS is mounted as / and doesn't have the same "read only filesystem" error.  Only samba has that.

---

### Post by bodhi.zazen on 2008-04-17
My understanding is data recovery from LVM can be difficult.

See if this helps at all :

[http://www.linuxjournal.com/article/8874](http://www.linuxjournal.com/article/8874)

---

### Post by handband2 on 2008-04-18
See if this post helps:
[http://ge.ubuntuforums.com/showpost.php?p=4087035&postcount=4](http://ge.ubuntuforums.com/showpost.php?p=4087035&postcount=4)

---

### Post by modnar0741 on 2008-04-18
I figured it would be difficult if not impossible.  That's why I didn't ask how to recover data.  My two questions were:
1) How do I identify which drive is malfunctioning.
This could be harder then it sounds.  I could reboot my computer and the failing hard drive may be working.  I wouldn't know.
2) How do i undo the damage done by fsck once I do the data recovery?
See, I'm assuming I'm able to do the recovery on my own.

---

### Post by bodhi.zazen on 2008-04-18
One other suggestion would be to try the Fedora Forums. I find people there helpful and Fedora uses LVM by default so perhaps you might find someone knowledgeable about LVM there.

---

