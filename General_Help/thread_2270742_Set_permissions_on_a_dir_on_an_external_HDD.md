---
title: "Set permissions on a dir on an external HDD"
date: 2015-03-25
forum: General Help
---

### Post by von Stalhein on 2015-03-25
I use an external HDD for backup. Crashplan is telling me the process fails becasue the destination isn't accessible.

I want to change the group permissions on a directory on the HDD to "access". At present it's "none".

Ive tried a heap of chmod commands etc with no luck so far.

The directory is located at ```
media/user$/drive/backup/
```

What should the command be to make the directory and the files in it "access"?

Thanks!

---

### Post by nerdtron on 2015-03-25
What permission do you need on the folder? read only or include write? An which user should you give it permissions.

If you want to give read/write (I assume write since you are going to save your backup). Just add the read/write permission on the folder using:
```
chmod g=rwx /media/user$/drive/backup
```

You will still have problems if your crashplan user is not a member of the groups that own the backup folder.

---

### Post by von Stalhein on 2015-03-29
Thanks - sorry for the late reply, I've been away.
No luck with that command - I want to set the Group to have read/write, at the moment it's only the Owner with that privelege.
 There is no indication in Teminal that the command doesn't work so I don't have any idea what the issue is.

---

### Post by Bashing-om on 2015-03-30
von Stalhein; Hello;

What is the filesystem on ' media/user$/drive/backup/ ' ... ? NTFS by chance ? IF so the Windows' permissions are not POSIX compliant .
These permissions are set in the mountpoint.
Show us what we are working with:
```

sudo fdisk -lu
sudo parted -l

```

Then we know a bit to make a recommendation.

[INDENT][INDENT]there is that way that seems right
[INDENT][INDENT][INDENT]but leads to a lot of trouble
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nerdtron on 2015-03-31
> **von Stalhein said:**
> Thanks - sorry for the late reply, I've been away.
No luck with that command - I want to set the Group to have read/write, at the moment it's only the Owner with that privelege.
 There is no indication in Teminal that the command doesn't work so I don't have any idea what the issue is.

And what is the output of the command?

---

### Post by von Stalhein on 2015-04-01
> **Bashing-om said:**
> von Stalhein; Hello;

What is the filesystem on ' media/user$/drive/backup/ ' ... ? NTFS by chance ? IF so the Windows' permissions are not POSIX compliant .
These permissions are set in the mountpoint.
Show us what we are working with:
```

sudo fdisk -lu
sudo parted -l

```

Then we know a bit to make a recommendation.
[INDENT][INDENT]there is that way that seems right[INDENT][INDENT][INDENT]but leads to a lot of trouble
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]



OK - yes, you're right :-)

```
Model: Seagate Expansion Desk (scsi)
Disk /dev/sdd: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ntfs

```
and

```
Disk /dev/sdd: 1.8 TiB, 2000398933504 bytes, 3907029167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc75b1e2d

```

---

### Post by von Stalhein on 2015-04-01
> **nerdtron said:**
> And what is the output of the command?

Yes, that was what I meant - there's no output from trying to chmod. it just goes to the next line with a command prompt.

---

### Post by nerdtron on 2015-04-01
> **von Stalhein said:**
> Yes, that was what I meant - there's no output from trying to chmod. it just goes to the next line with a command prompt.

No output means it executed correctly. Now we just need to check the permissions of your drive to see if you have write permissions:

```
id
ll -a /media/user$/drive/backup
```

---

### Post by von Stalhein on 2015-04-01
Thanks. The outputs of those commands below:
```
xxxx@xxxx:~$ id
uid=1000(xxxx) gid=1000(xxxx) groups=1000(xxxx),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),125(sambashare)


```

```
xxxx@xxxx:~$ ll -a /media/xxxx/"Seagate Expansion Drive"
total 2841
drwx------  1 xxxx xxxx    4096 Mar  1 19:58 ./
drwxr-x---+ 6 root    root       4096 Apr  1 17:33 ../
-rw-------  1 xxxx xxxx     182 Feb 23  2012 Autorun.inf
drwx------  1 xxxx xxxx  741376 Mar 26 03:22 Backup/
drwx------  1 xxxx xxxx  327680 Oct  3 10:59 Canon Backup 3Oct2014/
drwx------  1 xxxx xxxx       0 Mar  1 23:42 CRashPlanBack/
drwx------  1 xxxx xxxx    4096 Nov 30  2013 DBZ/
drwx------  1 xxxx xxxx    4096 Nov 14 09:48 videomovie/
drwx------  1 xxxx xxxx       0 Jul 26  2014 KathsPhone/
drwx------  1 xxxx xxxx    4096 Dec  2  2013 $RECYCLE.BIN/
drwx------  1 xxxx xxxx       0 Nov 28  2012 Seagate/
-rw-------  2 xxxx xxxx 1644118 Mar  5  2012 SeagateExpansion.ico
-rw-------  1 xxxx xxxx  156312 Jan 16  2009 Setup.exe
drwx------  1 xxxx xxxx    4096 Feb 18 17:59 System Volume Information/
drwx------  1 xxxx xxxx    4096 Sep 30  2014 Video/
drwx------  1 xxxx xxxx    4096 Sep 30  2014 WorkLaptop/


```

---

### Post by nerdtron on 2015-04-01
I'm assuming this xxxx:
uid=1000(xxxx) gid=1000(xxxx) groups=1000(xxxx)

is the same as the xxxx:

rwx------  1 xxxx xxxx    4096 Mar  1 19:58 ./
-rw-------  1 xxxx xxxx     182 Feb 23  2012 Autorun.inf
drwx------  1 xxxx xxxx  741376 Mar 26 03:22 Backup/
drwx------  1 xxxx xxxx  327680 Oct  3 10:59 Canon Backup 3


Then this means your user is the owner of the seagate drive folder. and you should be able to read/write on that folder.

Edit: Oppsss. you want groups to have read/write permissions too but I don't think the permissions from the previous command was applied.
You can try the chmod command again, then try to verify it again. If it still doesn't work, maybe you should change the mount options of the drive/

---

### Post by Bashing-om on 2015-04-01
von Stalhein; Welp;

I say again, one can not impose POSIX regulations on the Windows' NTFS file system. Those access rights for NTFS are set in the mount point. Generally established in the ' /etc/fstab '  file.
For example:
[http://askubuntu.com/questions/43570/change-owner-of-internal-hard-drive-partition-from-root-to-user](http://askubuntu.com/questions/43570/change-owner-of-internal-hard-drive-partition-from-root-to-user)

To set these rights as desired for your use case, see:
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
<-HOWTO: Mount NTFS partitions with specific ownership/permissions

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

