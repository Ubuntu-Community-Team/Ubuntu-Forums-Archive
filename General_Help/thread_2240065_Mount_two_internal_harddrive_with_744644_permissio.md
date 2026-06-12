---
title: "Mount two internal harddrive with 744/644 permission"
date: 2014-08-17
forum: General Help
---

### Post by texsas on 2014-08-17
Hi,

I'm having trouble mounting two internal harddrives with right permissions on my Ubuntu Desktop 14.04LTS.

When I Mount them with GUI i get 700-permission on folders and 600-permission on my files. I would like to have them 744 and 644 so my minidlna could access the files.

When I type df -T they are mounted as fuseblk.

fdisk -l say that my /dev/sdb1 is a W95 FAT32 System, 
and my /dev/sdc1 is a HPFS/NTFS/exFAT System.

I have edited /etc/fuse.conf With *u**ser_allow_other,* but they still have 700 and 600.

How can I mount these harddrives with right permissions?

Thanks in advance

---

### Post by nerdtron on 2014-08-17
FAT32 and NTFS partitions don't follow linux parititons so any files in these permissions will be readable to all users.
Post the output of "ls -lh" to see the file permissions of the files in the mounted partitions.

---

### Post by bab1 on 2014-08-17
> **texsas said:**
> Hi,

I'm having trouble mounting two internal harddrives with right permissions on my Ubuntu Desktop 14.04LTS.

When I Mount them with GUI i get 700-permission on folders and 600-permission on my files. I would like to have them 744 and 644 so my minidlna could access the files.

When I type df -T they are mounted as fuseblk.

fdisk -l say that my /dev/sdb1 is a W95 FAT32 System, 
and my /dev/sdc1 is a HPFS/NTFS/exFAT System.

I have edited /etc/fuse.conf With *u**ser_allow_other,* but they still have 700 and 600.

How can I mount these harddrives with right permissions?

Thanks in advance

You have to mount them manually or create a UDEV rule.  The user and group along with permissions are set at mount time.  Since this is not EXT the system will not know what to do.  You will also need to set the permissions with the mount command.  Here is the relevant part of the man page for the command *mount*```
man mount 
...

Mount options for fat
       (Note: fat is not a separate filesystem, but a common part of the msdos, umsdos  and  vfat
       filesystems.)

       blocksize={512|1024|2048}
              Set blocksize (default 512). This option is obsolete.

       uid=value and gid=value
              Set  the  owner  and  group of all files.  (Default: the uid and gid of the current
              process.)

       umask=value
              Set the umask (the bitmask of the permissions that are not present). The default is
              the umask of the current process.  The value is given in octal.

       dmask=value
              Set the umask applied to directories only.  The default is the umask of the current
              process.  The value is given in octal.

       fmask=value
              Set the umask applied to regular files only.  The default is the umask of the  cur&#8208;
              rent process.  The value is given in octal.



```

---

### Post by bab1 on 2014-08-17
> **nerdtron said:**
> FAT32 and NTFS partitions don't follow linux parititons so any files in these permissions will be readable to all users.
Post the output of "ls -lh" to see the file permissions of the files in the mounted partitions.
This doesn't even make any sense.  A FAT partition is mounted using the appropriate driver (module) to handle the permissions.  Those permission options are utilized when the FAT partition is mounted.  Typically on the latest versions of Ubuntu the logged in user is the owner and the only one with permissions (I.E.  0700 and 0600).

---

### Post by nerdtron on 2014-08-17
Hmm.. That's weird, I just did "ls -lh" on my ntfs partition and permissions are set to 777 for both files and dirs.
And I just mounted it using the generic command like "mount /dev/sdb2 /media/ntfs". Filesystem type was automatically detected as ntfs.
And this is a server 12.04.

---

### Post by bab1 on 2014-08-17
> **nerdtron said:**
> Hmm.. That's weird, I just did "ls -lh" on my ntfs partition and permissions are set to 777 for both files and dirs.
And I just mounted it using the generic command like "mount /dev/sdb2 /media/ntfs". Filesystem type was automatically detected as ntfs.
And this is a server 12.04.
A lot depends upon your environment. [COLOR="#0000FF"]Edit: For instance mount won't work as you stated unless you are the root  user -- that is not a normal thing with Ubuntu. Here is a ***blkid*** listing of a small NTFS partition that I have mounted at /media[/COLOR]```
[COLOR="#0000FF"]/dev/sdb1          ntfs      PAT32GB    /media/PAT32GB         4AE48D61526110000[/COLOR]
``` 

If you read the man pages you will see you should use mount -t nfts or mount -t ntfs-3g to mount NTFS partitions.  ```
 The command

                     mount -a [-t type] [-O optlist]

...

       -t, --types vfstype
              The  argument  following  the  -t  is  used  to  indicate the filesystem type.  The
              filesystem types which are currently supported include: adfs, affs,  autofs,  cifs,
              coda,  coherent, cramfs, debugfs, devpts, efs, ext, ext2, ext3, ext4, hfs, hfsplus,
              hpfs, iso9660, jfs, minix, msdos, ncpfs, nfs, nfs4, ntfs, proc, qnx4, ramfs,  reis&#8208;
              erfs,  romfs,  squashfs,  smbfs, sysv, tmpfs, ubifs, udf, ufs, umsdos, usbfs, vfat,
              xenix, xfs, xiafs.  Note that coherent, sysv and  xenix  are  equivalent  and  that
              xenix  and coherent will be removed at some point in the future &#8212; use sysv instead.
              Since kernel version 2.1.21 the types ext and xiafs do not exist anymore.  Earlier,
              usbfs  was  known  as  usbdevfs.   Note, the real list of all supported filesystems
              depends on your kernel.


```

I might point out the FAT and NTFS only have one thing in common.  They were both created by Microsoft.  You should never rely on the fact that "it works today".  Tomorrow may be a different thing.  The proper way should always work.

[COLOR="#0000FF"]Edit2:  I have remounted the NTFS partition I have as a root user but without specifying the file system format and indeed it incorrectly mounts the partition as rwx for all users.  This is an unintended action (a bug if you will).  A user that mounts an NTFS partition like this can expect erratic behavior.  My vote is to mount it correctly (mount -t ntfs) and control access as intended.  Thanks to @nerdtron for pointing out the bug.[/COLOR]

---

### Post by texsas on 2014-08-21
Well, I see that using Fat32 and NTFS is not a good idea. 
I'm going to format these harddrives to ext4. Then these problems should be gone :)

Thanx for replies

---

