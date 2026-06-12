---
title: "External USB HDD Suddenly Can't Be Mounted"
date: 2016-08-29
forum: General Help
---

### Post by DeadlyOats on 2016-08-29
I had used this drive without issues, just last week.  When I tried mounting it again, a few days ago, I got an error message that I could not mount the drive. Since then, I rebooted my PC and then, today tried to mount the drive again.  This is the error message I'm getting:

> An error occurred while accessing 'Externalusbdrivenname', the system responded: The requested operation has failed: Error mounting /dev/sdc1 at /media/myusername/Externalusbdrivenname: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdc1" "/media/myusername/Externalusbdrivenname"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

I ran dmesg | tail and got:

> myusername@MYCOMPUTER'SNAME:~$ dmesg | tail
[219615.527850] sd 8:0:0:0: [sdb] tag#0 Add. Sense: No additional sense information
[219615.527853] sd 8:0:0:0: [sdb] tag#0 CDB: ATA command pass through(12)/Blank a1 06 20 da 00 00 4f c2 00 b0 00 00
[220215.413106] sd 8:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[220215.413112] sd 8:0:0:0: [sdb] tag#0 Sense Key : Hardware Error [current] [descriptor] 
[220215.413115] sd 8:0:0:0: [sdb] tag#0 Add. Sense: No additional sense information
[220215.413120] sd 8:0:0:0: [sdb] tag#0 CDB: ATA command pass through(16) 85 06 20 00 00 00 00 00 00 00 00 00 00 00 e5 00
[220215.500093] sd 8:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[220215.500097] sd 8:0:0:0: [sdb] tag#0 Sense Key : Hardware Error [current] [descriptor] 
[220215.500098] sd 8:0:0:0: [sdb] tag#0 Add. Sense: No additional sense information
[220215.500101] sd 8:0:0:0: [sdb] tag#0 CDB: ATA command pass through(12)/Blank a1 06 20 da 00 00 4f c2 00 b0 00 00


I tried running dmesg | so and got:

> myusername@MYCOMPUTER'SNAME:~$ dmesg | so
so: command not found

What does this all mean? And how do I fix this so that I can mount my external usb hdd again?

---

### Post by Jimysbil on 2016-08-29
Open a terminal and type:
```
sudo su
```
[COLOR=#ff0000]* This command with give you root access.Be careful![/COLOR]

Type
```
fsck.ext4 -v /dev/sdc1
```

If you see an output like this
```
fsck.ext4: Group descriptors look bad... trying backup blocks...

fsck.ext4: Bad magic number in super-block while trying to open /dev/sdc1
The superblock could not be read or does not describe a correct ext4
filesystem.  If the device is valid and it really contains an ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193
```
you probably have a bad Superblock.

In order to fix it type the command:
```
mke2fs -n /dev/sdc1
```
[COLOR=#ff0000]** This command with give you a list of backups for your Superblock.[/COLOR]

Copy one of the printed numbers and execute a command like this:
```
e2fsck -b (your block number} /dev/sdc1
```

Try to reboot and your Superblock should be fixed.If not, execute the command again with a different Superblock number this time.
[COLOR=#ff0000]*** Remember to unmount your external drives before you disconect them from your PC.[/COLOR]

---

### Post by mook765 on 2016-08-29
> mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdc1" "/media/myusername/Externalusbdrivenname"
Looks like bad syntax.
Shouldn't it be
> mount -t ext4 -o uhelper=udisks2,nodev,nosuid /dev/sdc1 /media/myusername/Externalusbdrivenname
?

---

### Post by Jimysbil on 2016-08-29
Something I forgot to ask you..What is the format of the partition on your external drive??I assume you have only one partition.So it makes me think it could be an NTFS.But according to your error my conclusion is that it's formated as ext4.

---

### Post by DeadlyOats on 2016-08-29
Here's what I got.

> myusername@MYCOMPUTER'SNAME:~$ sudo su
[sudo] password for myusername: 
root@MYCOMPUTER'SNAME:/home/myusername# fsck.ext4 -v /dev/sdc1
e2fsck 1.42.13 (17-May-2015)
Externalusbdrivenname: recovering journal
Externalusbdrivenname contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

       73569 inodes used (0.40%, out of 18317312)
        2108 non-contiguous files (2.9%)
           1 non-contiguous directory (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 73496/62
    59480307 blocks used (81.19%, out of 73256392)
           0 bad blocks
           8 large files

       66222 regular files
        7337 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
           1 symbolic link (1 fast symbolic link)
           0 sockets
------------
       73560 files
root@MYCOMPUTER'SNAME:/home/myusername# 


I went ahead and tried mounting the drive again, after that, and it mounted. Problem fixed.

THANK YOU, SO VERY MUCH!!!

EDIT:

Yes, I had it formatted with the ext4 file system.

---

