---
title: "Folder is not writable by user root"
date: 2018-10-15
forum: General Help
---

### Post by tritonal on 2018-10-15
I've recently installed Radarr on Ubuntu 18.04. It has 5 internal Hard drives but drive1 seems to be giving me a lot of issues. I have all drives mounted to /home/ as
  /home/drive1/
  /home/drive2/ Etc
  When I go to add /home/drive1/Movies folder using the bulk importer I get the error "Folder is not writable by user root"
  All other drivers are working just fine in Radarr and Sonnar, just not this one.
  When using sudo chown -R server:server /home/drive1/ I get
  chown: changing ownership of '/home/drive1/': Read-only file system
  And when using sudo chmod 777 /home/drive/ I get
  chmod: changing permissions of '/home/drive1/': Read-only file system
 
 

Using the 'Disks' tool I ran a check on the drive and it checked fine. The mount options are nosuid,nodev,nofail,x-gvfs-show which match all of the other drives.

---

### Post by TheFu on 2018-10-15
Which file system do each have?
Where the file systems shutdown cleanly?  Linux will mount read-only unclean file systems as a way to protect them from further damage.
gfvs mounts are slow. Best avoided except for quick, temporary uses.

---

### Post by tritonal on 2018-10-15
All of the drives except the one giving me issues show as NTFS/exFAT/HPFS under partition type. The drive giving issues shows as basic data for partition type and NTFS under contents. The drive were previously used under Windows 10.

---

### Post by TheFu on 2018-10-15
Permissions don't work under NTFS, so chmod won't do anything.
If the Windows disks aren't "simple volumes", then I don't think any Linux will be able to use it.  
If the drive wasn't completely, properly, dismounted by the Windows system, Linux won't touch it.  Connect it to a Windows system and manually unmount it.

The only way to control users, groups and permissions on NTFS partitions is through mount options by specifying the user, group, and file masks to be used.

The output from **sudo fdisk -l** would be very helpful as proof.  Please  use code tags so that output is readable and lines up in columns.

---

### Post by tritonal on 2018-10-15
Here's the output of fsdisk -l.


```

[sudo] password for server: 
Disk /dev/loop0: 2.3 MiB, 2433024 bytes, 4752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 14.5 MiB, 15208448 bytes, 29704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 34.7 MiB, 36323328 bytes, 70944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 86.9 MiB, 91099136 bytes, 177928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 4.9 MiB, 5148672 bytes, 10056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 87.9 MiB, 92119040 bytes, 179920 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 42.1 MiB, 44183552 bytes, 86296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 64B7405B-27EB-423E-876E-AD71947E636C

Device      Start        End    Sectors  Size Type
/dev/sda1      34     262177     262144  128M Microsoft reserved
/dev/sda2  264192 7814035455 7813771264  3.7T Microsoft basic data

Partition 1 does not start on physical sector boundary.


Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xb7fef16b

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdb1        2048 3907026943 3907024896  1.8T  7 HPFS/NTFS/exFAT


Disk /dev/sdc: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x03454243

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdc1  *     2048 500117282 500115235 238.5G 83 Linux


Disk /dev/sdd: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xb7fef16a

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdd1        2048 3907026943 3907024896  1.8T  7 HPFS/NTFS/exFAT


Disk /dev/sde: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x55eca64c

Device     Boot Start        End    Sectors   Size Id Type
/dev/sde1        2048 1953521663 1953519616 931.5G  7 HPFS/NTFS/exFAT


Disk /dev/sdf: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc2bd658e

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdf1  *     2048 1953521663 1953519616 931.5G  7 HPFS/NTFS/exFAT


Disk /dev/loop8: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 3.7 MiB, 3887104 bytes, 7592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 4.7 MiB, 4919296 bytes, 9608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 14.5 MiB, 15196160 bytes, 29680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 10.1 MiB, 10571776 bytes, 20648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 3.7 MiB, 3878912 bytes, 7576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 140.9 MiB, 147722240 bytes, 288520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 2.3 MiB, 2355200 bytes, 4600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

Unfortunatley I don't have any way of connecting these drives to a windows machine. Would I be better just completely reformatting them? If I back up the files to another drive, reformat that drive then move the files back will I still have this issue?

---

### Post by TheFu on 2018-10-15
First, all the loop devices are just clutter in the fdisk output. If you remove them, people won't be distracted and make mistakes.  They are caused by using "snaps" for package installs.

Second, sda, has this warning:
> Partition 1 does not start on physical sector boundary.
That means that accessing files on sda1 is misaligned and between 10 and 30% slower than it should be.

This is what I would do.  I don't know if it is a good idea for you situation, but if you don't have Windows, then you don't need NTFS.
I would get some new storage, format the new storage with ext4, then copy everything off the misaligned NTFS storage to the new EXT4 storage.  Then I'd wipe that NTFS storage, create a fresh partition table using GPT, not MBR, and create a new EXT4 file system.  Then I'd move to the next NTFS disk, copy over all the data to the new GPT+EXT4 disk.  Then do that over and over for the remaining disks.

I didn't look carefully at the disk sizes, but if the new storage is larger than any of the the other disks you have, it shouldn't be an issue.  I think 2TB disks are $45 now.  Ah .. sda is 4TB.  I've seen 8TB disks for $140 recently, but I would only buy either an HTS or WD disk and avoid any other options.  Actually, I have a rule that if I can't buy 2 disks of the same size, then I won't use any of the storage. 1 is primary, holding data and the other is a backup copy.  This is my rule for media.  For non-media files, I use normal, versioned, backups to a 2TB disk on a backup server.  For the OS and all those little files, emails, documents, on a desktop, I keep 60 days of versioned backups.  For higher risk servers, I keep 180 days of versioned backups.  But for media, I keep 1 mirror that is maintained every few days using rsync.

ext4 provides native Unix file permissions, owners, groups and ACLs. chown + chmod work.  If you want more protection than ext4 provides, consider using ZFS, but beware that ZFS does being complexities.  I'm not qualified to make suggestions for ZFS storage layout considerations. I probably wouldn't use ZFS over USB connections - only SATA or eSATA or with internal NVMe storage.

---

### Post by tritonal on 2018-10-15
The amount of data I need to save on that drive is only around 700gb right now. I have a 1TB external I can format to EXT4 then transfer the files over, format the drive, restore the files and then rinse and repeat with the rest of them. It'll be a lengthy process but Should be done today hopefully. Should I do all the formatting from inside ubuntu or use Gparted?

---

### Post by TheFu on 2018-10-15
Step 1: GPT partition (not MBR)  You'll thank me later
Step 2: Create EXT4 partition
Step 3: Format new partition as EXT4
Step 4 (optional) Reduce the "reserved blocks" for any "data partitions" from 5% to 1%. NEVER do this for OS or /home partitions, but for DATA partitions it is foolish to waste 5% of the disk, right?  On a 4TB disk, 5% is 200G! **tune2fs** is the tool.

Gparted is fine, but you can use any tool you like.
Triple check that you have all the data moved, accurately before doing the new GPT partition table step. It is gone after that.  Lots of people in these forums are very unhappy when they make mistakes.  Linux does what we tell it to do, even if we don't understand the repercussions and data loss it will cause.

---

### Post by tritonal on 2018-10-15
Alright I managed to complete the steps above using gparted. But I can not copy the files over. When I try it says I don't have permissions to create it in the destination. chmod and chown didn't change anything on the external drive. I can try reformating again to see if that helps.

---

### Post by TheFu on 2018-10-15
If you already did things correctly, why would doing them again make any difference?  I'm just curious.

Instead of claiming what you did, please try to show proof that you fixed the ownership and permissions.  PROOF.

That would be using these sorts of commands **on the appropriate file systems.**
```
df -hT
ls -al
```

---

### Post by tritonal on 2018-10-15
The reasoning for trying again is in case I jacked up before.

Heres df -hT
```
server@server-desktop:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.8G     0  3.8G   0% /dev
tmpfs          tmpfs     768M  1.8M  766M   1% /run
/dev/sdc1      ext4      234G   18G  205G   8% /
tmpfs          tmpfs     3.8G   12K  3.8G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     3.8G     0  3.8G   0% /sys/fs/cgroup
/dev/loop0     squashfs  2.4M  2.4M     0 100% /snap/gnome-calculator/180
/dev/loop2     squashfs   35M   35M     0 100% /snap/gtk-common-themes/319
/dev/loop1     squashfs   15M   15M     0 100% /snap/gnome-logs/45
/dev/loop3     squashfs   87M   87M     0 100% /snap/core/4917
/dev/loop4     squashfs  5.0M  5.0M     0 100% /snap/canonical-livepatch/50
/dev/loop5     squashfs   13M   13M     0 100% /snap/gnome-characters/103
/dev/loop6     squashfs   88M   88M     0 100% /snap/core/5548
/dev/loop7     squashfs   43M   43M     0 100% /snap/gtk-common-themes/701
/dev/loop8     squashfs   13M   13M     0 100% /snap/gnome-characters/124
/dev/loop9     squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/51
/dev/loop10    squashfs  4.8M  4.8M     0 100% /snap/canonical-livepatch/49
/dev/loop11    squashfs   15M   15M     0 100% /snap/gnome-logs/37
/dev/loop13    squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/57
/dev/loop12    squashfs   11M   11M     0 100% /snap/glances/5
/dev/loop14    squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/loop15    squashfs  2.3M  2.3M     0 100% /snap/gnome-calculator/238
tmpfs          tmpfs     768M   56K  768M   1% /run/user/1000
/dev/sdf1      fuseblk   932G  533G  400G  58% /home/drive5
/dev/sde1      fuseblk   932G  242G  691G  26% /home/drive4
/dev/sdb1      fuseblk   1.9T  620G  1.3T  34% /home/drive2
/dev/sdd1      fuseblk   1.9T  930G  934G  50% /home/drive3
/dev/sda2      fuseblk   3.7T  724G  3.0T  20% /home/drive1
/dev/sdg1      ext4      916G   72M  870G   1% /media/server/adc7c8b5-c62c-45e1-b093-864003c2a7c6


```
and ls -al
```
server@server-desktop:~$ ls -al
total 7124
drwxr-xr-x 21 server server    4096 Oct 15 13:07 .
drwxr-xr-x  9 server server    4096 Oct  9 13:21 ..
-rw-rw-r--  1 server server     125 Oct  9 13:57 .apport-ignore.xml
-rw-------  1 server server   10159 Oct 15 13:22 .bash_history
-rw-r--r--  1 server server     220 Oct  7 16:15 .bash_logout
-rw-r--r--  1 server server    3771 Oct  7 16:15 .bashrc
drwx------ 20 server server    4096 Oct 15 13:07 .cache
drwx------ 20 server server    4096 Oct  8 09:48 .config
drwxr-xr-x  2 server server    4096 Oct  7 16:18 Desktop
drwxr-xr-x  2 server server    4096 Oct 14 20:18 Documents
drwxr-xr-x  3 server server    4096 Oct 14 19:52 Downloads
-rw-r--r--  1 server server    8980 Oct  7 16:15 examples.desktop
drwx------  3 server server    4096 Oct  7 16:37 .gnupg
-rw-------  1 server server    8738 Oct 15 08:04 .ICEauthority
drwx------  3 server server    4096 Oct  7 16:18 .local
drwx------  5 server server    4096 Oct  7 16:21 .mozilla
drwxr-xr-x  2 server server    4096 Oct  7 16:18 Music
drwxr-xr-x  2 server server    4096 Oct  7 16:18 Pictures
drwxr-xr-x  2 server server    4096 Oct  7 16:43 plexmedia
-rw-r--r--  1 server server     807 Oct  7 16:15 .profile
drwxr-xr-x  2 server server    4096 Oct  7 16:18 Public
drwxr-xr-x  4 server server    4096 Oct  7 18:50 Radarr
-rw-r--r--  1 server server 7071497 May 25  2017 Radarr.develop.0.2.0.299.linux.tar.gz
drwxrwxr-x  4 server server    4096 Oct  7 18:42 .sabnzbd
drwxr-xr-x  4 server server    4096 Oct  7 18:07 snap
-rw-------  1 server server   12288 Oct  7 20:50 .sonarr.service.swm
-rw-------  1 server server   12288 Oct  7 20:49 .sonarr.service.swn
-rw-------  1 server server   12288 Oct  7 20:48 .sonarr.service.swo
-rw-------  1 server server   12288 Oct  7 20:52 .sonarr.service.swp
drwx------  2 server server    4096 Oct  7 16:37 .ssh
-rw-r--r--  1 server server       0 Oct  7 16:27 .sudo_as_admin_successful
-rw-------  1 server server   12288 Oct  7 17:00 .swp
drwxr-xr-x  2 server server    4096 Oct  7 16:18 Templates
drwx------  4 server server    4096 Oct 15 13:07 .thunderbird
drwxr-xr-x  2 server server    4096 Oct  7 16:18 Videos
-rw-------  1 server server    9072 Oct  7 22:22 .viminfo
-rw-r--r--  1 server server     165 Oct  7 18:49 .wget-hsts

```

The external drive I am attempting to use to for backups is /dev/sdg1

---

### Post by SeijiSensei on 2018-10-15
Can you copy the files as the root user with sudo?

---

### Post by tritonal on 2018-10-15
No when I use sudo mv /home/drive1/Movies /media/server/abc7c8b5-c62c-45e1-b093-864003c2a7c6 it creates a new folder with the same name as the drive in /media/server/. I've had mild success moving files by instead of selecting the drive directly in the file explore. I navigate to /media/server/abc7c8b5-c62c-45e1-b093-864003c2a7c6 but it only movies 3 or 4 files and thats it.

Edit - I've tried again and it actually seems to be transfering now with sudo. Not sure why before it'd only transfer a few files then stop.

---

### Post by TheFu on 2018-10-15
**ls -al /media/server/adc7c8b5-c62c-45e1-b093-864003c2a7c6**
is actually what I intended.  Also, all the 'loop' devices are just cruft.

I don't use GUIs to move/copy files around.  They hide feedback when there are issues.

Diagnosing problems without actual, exact, error messages and the exact command used  is difficult.  Often, putting the error messages into google will yield a solution, for example.
I would use this:
```
sudo mv -v /home/drive1/Movies /media/server/abc7c8b5-c62c-45e1-b093-864003c2a7c6/
```
The trailing slash is a good habit, since you might want to use rsync at some point and the trailing slash means different things, completely.

If things aren't working and the shell version output isn't providing sufficient feedback, normally the commands have a way to ask for more output - either debug or verbosity.  And always check the system logs for issues.  Failures for a copy could easily be a bad USB connection, which would show up in the log files.

On the old days, mv wouldn't work across different file systems and definitely not to different disks.  We had to copy stuff over, then go back and delete the stuff we didn't want, manually.  OTOH, using mv on the same file system is nearly instantaneous, because of what it actually does under the covers.

---

### Post by tritonal on 2018-10-15
Sorry about that, here is the ls-al
```
server@server-desktop:~$ ls -al /media/server/adc7c8b5-c62c-45e1-b093-864003c2a7c6
total 28
drwxrwxrwx  4 server server  4096 Oct 15 16:01 .
drwxrwxrwx+ 6 root   root    4096 Oct 15 14:14 ..
drwxrwxrwx  2 root   root   16384 Oct 15 10:17 lost+found
drwx------  4 server server  4096 Oct 15 14:53 .Trash-1000


```

It seems to be moving files just insanely slow. I'll let it sit through the night and hopefully it finishes transfering then get to work on the other drives. Thanks alot for your help.

---

### Post by TheFu on 2018-10-15
Do you see the permissions problems?  Seems pretty clear from here.

BTW, I used the sudo in my last post because SeijiSensei suggested it. It would work, but isn't how I'd do it.  I'd make a top level directory to hold things and move all the stuff into there.  If any of the storage is connected over USB2, that will be REALLY slow.  If any of the storage is NTFS, there are tuning options like big_writes to help performance.  Don't let GVFS or FUSE be used for storage if you want performance.
From the mount.ntfs manpage:```

       big_writes
              This option prevents fuse from splitting write buffers  into  4K
              chunks,  enabling  big  write buffers to be transferred from the
              application in a single step (up to some system limit, generally
              128K bytes).
```

If you can, use SATA or eSATA connections instead of USB-anything.  If both source and target use the same USB hub, you'll see much less throughput.

And for copying/moving lots of files, I'd use rsync.

---

