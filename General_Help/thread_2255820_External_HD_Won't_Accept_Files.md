---
title: "External HD Won't Accept Files"
date: 2014-12-07
forum: General Help
---

### Post by Smallwheels on 2014-12-07
I want to move all of the files from one external drive to a different external drive. 
One is working just fine. The other was working too. 

To start I used GPartED to reformat the drive of the secondary external HDD. It is in EXT4. I left 1 MB space ahead of the partition when doing it. After all was done I tried to copy and paste the folders of one drive into the new one. I got an error message for every file. I just kept pressing the Skip button until there were no more files. Then I tried copying and pasting individual files. The same error message pops up with the file name. 

Nothing can be added to this drive. I tried going to a web page and saving an image to the new drive. It went through the motions just as would happen using my other drive yet nothing appeared in the new drive folder.  

The error message says, "Error while copying "file name" There was an error copying the file into /media/af806fb9-1c24-416f-add5-4e3dd1f3d245." 
In the details section it further says "Error opening file '/media/af806fb9-1c24-416f-aee5-4e3dd1f3d245/file name': Permission denied"

I don't know what all of those gobbledy gook /media... stuff are. They aren't part of the file names. 

This secondary drive needs to be fixed pronto. I want to store my data in it before I take the other drive on the road with me. The other one will be the backup. 

An extra question or two are why is my 500 GB HDD showing just 465 GB free out of 492 GB? It says 5% is in use. How can I get full use of the 492? What is using up all of that space beyond the 465 GB? 

As an extra bit of information the secondary HDD has a file already in it. It is labeled "lost+found" and it won't allow me to open it. I don't know what that is either. 

Thank you.

---

### Post by oldos2er on 2014-12-07
The long alphanumeric string "af806fb9-1c24-416f-aee5-4e3dd1f3d245" is a [UUID]("https://help.ubuntu.com/community/UsingUUID"). the lost+found folder is a normal part of an ext4 partition, it's where files recovered using fsck (if any) are stored.

Your user can take ownership of an ext4 partition with the following command. Replace "user" with your user account name. ```
sudo chown -R user:user /media/af806fb9-1c24-416f-aee5-4e3dd1f3d245
```

---

### Post by Smallwheels on 2014-12-07
Thank you Ann. Is my user account name my password? If not then how do I set up a user account name or find the existing one?

---

### Post by xubu2 on 2014-12-07
Have you tried giving yourself sudo rights to the HD with:
```
sudo chown <YOURNAME>:users /media/<YOURNAME>/<NAMEHD>
```

Edit: Somebody beat me to it :)

---

### Post by Bucky Ball on 2014-12-07
> **Smallwheels said:**
> Thank you Ann. Is my user account name my password? If not then how do I set up a user account name or find the existing one?

If you open a terminal you will see:

your_username@your_computer_name

Where 'your_username' is what you want to put in the command that Ann provided where you see 'user:user'.

For instance:

```
sudo chown -R bucky:bucky /media/af806fb9-1c24-416f-aee5-4e3dd1f3d245
```

---

### Post by Smallwheels on 2014-12-07
Sorry. It isn't working. Here is what I'm typing:```
sudo chown -r michael:user  /media/af806fb9-1c24-416f-add5-4e3dd1f3d245


```
I also tried this:

```
sudo chown michael:users /media/af806fb9-1c24-416f-add5-4e3dd1f3d245/michael/500 GB Filesystem

```
500 GB Filesystem is the name that is popping up on my file manager window. 

This is what pops up as my file name but not all of the digits. I left a few out. michael@michael-NY801AV-ABA- Should I be including all of this as my user name or just the michael before the @ symbol?

---

### Post by Bucky Ball on 2014-12-07
You want:

michael:michael

NOT:

michael:user

;)

No digits. You just want the user. The other bit is your machine's name.

---

### Post by Smallwheels on 2014-12-07
I'm still trying. I keep getting messages saying no such file or directory. I even changed the name of the external drive so it had no spaces. Now I'm going to shut everything off and reboot the machine so that maybe it will recognize the drive. I can't get it to mount.

---

### Post by Smallwheels on 2014-12-07
Now that I have renamed the HDD I needed to try the file transfer again to see what name comes up. I'm stil failing at it but now this is the new name with the name of the image file: "Error opening file '/media/G_TECH/SANY0146.JPG': Permission denied"

This is what I ended up typing::```
sudo chown michael:michael /media/G_TECH
```
It seems to be working. 

An important question is how will this new backup drive work when I connect it to a different computer? I have a laptop that can recognize EXT 4 files for now. Will it also be able to recognize these files? If not what will I need to do to it? It is a Chromebook. The computer I'm using now will be sold or given away in the next week. This backup needs to work with other computers.

---

### Post by Bucky Ball on 2014-12-07
Well, a Windows machine won't recognise EXT4 partitions. Linux boxes will without issue.

---

### Post by Smallwheels on 2014-12-08
My Chromebook does read and allow me to transfer files to the EXT4 external drive I have now. The G TECH drive wouldn't allow me to add files to it until I did the chown business. Will I have to go through this again on all non-windoz machines I plug the G TECH into? I have no intention of using any Windoz machines. I like my Chromebook and intend to get another one and put a variant of GNU/Linux on it.

---

### Post by Bucky Ball on 2014-12-08
Unsure. Are you connecting the external drive via USB? It is a puzzle why it is not mounting automagically if that is the case. All things as they should be, it would be a matter of plugging it in and switching it on and it should mount like any other USB device. eSATA can be another matter, though. I have had trouble with that in the past and it was a long road working out how to get it happening.

---

### Post by Smallwheels on 2014-12-08
During the process of figuring out this problem I turned off the machine and rebooted it. At first neither the G TECH nor my other external HDD would mount. I turned things on and off and eventually they did mount. Their names appeared but I couldn't access them for a while. Then I could. 

Both of these external drives are connected via USB 2. Months ago I stopped storing anything on the internal HDD because I knew I would be selling it or giving it away. All of my data is on the external drive. I wanted to copy that data before going on a trip. There will be times when I need to leave the drive in a hotel room. If it gets stolen I want to have a copy. It is the sensible thing to do. When the copy is complete (sometime overnight at 11.3 MB/second) I will try connecting the G TECH drive to the Chromebook and see what happens. 

As a bit of extra information, Chrome OS has a way to format external media. It just gives the user a choice to reformat. It doesn't offer any file types. It automatically converts drives to FAT 32. That was disappointing. At least I know it reads EXT 4 for now. There is talk on the Chromebook forums that Google will only support NTFS and Fat 32 in the future. Many people will be disappointed if that happens.

---

### Post by oldos2er on 2014-12-08
> **Smallwheels said:**
> Ann do you have any idea how I can reclaim that 27 GB of space? 492-465.

ext4 reserves 5% of its partition for use by the root account and system services, but you can change that value if you wish, see [http://www.microhowto.info/howto/reduce_the_space_reserved_for_root_on_an_ext2_ext3_or_ext4_filesystem.html](http://www.microhowto.info/howto/reduce_the_space_reserved_for_root_on_an_ext2_ext3_or_ext4_filesystem.html)

---

### Post by Smallwheels on 2014-12-08
Thank you for the article Ann. It isn't working for me. I must be typing the wrong thing or not enough information.

At first I tried the command with the name G_Tech. That didn't work. Then I opened GPartED and looked for the name it was using for that partition. Maybe I was selecting the wrong partition. The only one listed was the /dev/sdb1. I inserted that name and it just gave me a message ```
tune2fs 1.42 (29-Nov-2011)
```
```
tune2fs: Permission denied while trying to open /dev/sdb1 Couldn't find valid filesystem superblock.
```

Since I'm using EXT4 and not 2 or 3 should I be entering ```
tune4fs -m 0 /dev/sdb1
```? That is, entering the 4 where the 2 was on the instructions. The instructions on the page didn't mention doing that. 

The partition I'm naming is the large one. Will this one get bigger or must I name the 5% section of the partition and work with that? I actually don't see any other partition when viewing the GUI in GPartED. Should I leave off the 1 when I type in sdb1? That would be the whole drive wouldn't it? That is what I tried the first time before adding the 1. Neither worked.

---

### Post by oldos2er on 2014-12-09
tune2fs works on all ext type partitions, there is no "tune4fs" command that I'm aware of. Also since you're making a significant change in your system you'll need to use sudo with tune2fs. I sure hope you have any necessary data backed up before proceeding.

We just need to find the correct block device. Can you post the output of both these commands? ```
sudo fdisk -l

mount
```

---

### Post by Smallwheels on 2014-12-09
```
[sudo] password for michael: fdisk: invalid option -- '1'
Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks


Options:
 -b <size>             sector size (512, 1024, 2048 or 4096)
 -c[=<mode>]           compatible mode: 'dos' or 'nondos' (default)
 -h                    print this help text
 -u[=<unit>]           display units: 'cylinders' or 'sectors' (default)
 -v                    print program version
 -C <number>           specify the number of cylinders
 -H <number>           specify the number of heads
 -S <number>           specify the number of sectors per track



```
And
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/home/michael/.Private on /home/michael type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=c0aad6c224f109de,ecryptfs_fnek_sig=20be35de5facc011)
gvfs-fuse-daemon on /home/michael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael)
/dev/sdb1 on /media/TOSHIBA EXT type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)



```

---

### Post by oldos2er on 2014-12-10
That's a letter l (ell), not a number 1 on *sudo fdisk -l*

---

### Post by Smallwheels on 2014-12-10
Here is the correct information with the L instead of the numeral 1.
```
[COLOR=#000000][FONT=Ubuntu Mono]Disk /dev/sda: 320.1 GB, 320072933376 bytes255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors[/FONT][/COLOR][COLOR=#000000]Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065b79


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   620951551   310474752   83  Linux
/dev/sda2       620953598   625141759     2094081    5  Extended
/dev/sda5       620953600   625141759     2094080   82  Linux swap / Solaris


Disk /dev/sdb: 1000.2 GB, 1000204883968 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525164 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x86b90b88


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1          206848  1953520064   976656608+   7  HPFS/NTFS/exFAT


Disk /dev/mapper/cryptswap1: 2144 MB, 2144337920 bytes
255 heads, 63 sectors/track, 260 cylinders, total 4188160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a442c88


Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table


Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f35c3


   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1            2048   976773119   488385536   83  Linux

[/COLOR]
[COLOR=#000000][/COLOR]
```

This is the bit after mount:
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/home/michael/.Private on /home/michael type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=c0aad6c224f109de,ecryptfs_fnek_sig=20be35de5facc011)
gvfs-fuse-daemon on /home/michael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael)
/dev/sdb1 on /media/TOSHIBA EXT type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)



```Maybe this will get the job done. Thank you.

---

### Post by oldos2er on 2014-12-11
tune2fs won't work on an NTFS partition (dev/sdb1), so I'm a bit unsure of what exactly you want to do.

---

### Post by Smallwheels on 2014-12-11
> **oldos2er said:**
> tune2fs won't work on an NTFS partition (dev/sdb1), so I'm a bit unsure of what exactly you want to do.
I do see the letters NTFS. Perhaps that is just a record of past information. The drive is formatted in EXT4. Opening GPartED shows that it is using EXT4. What I want to do is remove that folder that is taking up 5% of the drive space as you explained earlier in the thread. 

As I look at it in GPartED the partition is named /dev/sdg1 if that helps.

---

### Post by oldos2er on 2014-12-11
> **Smallwheels said:**
> I do see the letters NTFS. Perhaps that is just a record of past information. 

No, the information is current when the command is run.

> **Smallwheels said:**
> The drive is formatted in EXT4. Opening GPartED shows that it is using EXT4. What I want to do is remove that folder that is taking up 5% of the drive space as you explained earlier in the thread. 

As I look at it in GPartED the partition is named /dev/sdg1 if that helps.

So it wasn't mounted when I had you run the previous commands. If you're certain it's /dev/sdg1, then use ```
tune2fs -m 0 /dev/sdg1
```

---

### Post by Smallwheels on 2014-12-11
Hello oldos2er. I just tried using that command with and without the external drive being mounted. I get this message:```
tune2fs: Permission denied while trying to open /dev/sdg1Couldn't find valid filesystem superblock.
```
This is what appears on the GPartED GUI when I open it and select the drive:

Partition /dev/sdg1 with a lock symbol
File System ext4
Mount Point /media/G_TECH
Label G_TECH
size 465.76
Used 247.03 GiB
Unused 208.73 GiB
Flags (nothing showing)

Have I been using the wrong name?

---

### Post by oldos2er on 2014-12-12
With the external drive plugged in to your computer and powered up, can you re-run [i[sudo fdisk -l[/i] and post the output?

---

### Post by Smallwheels on 2014-12-12
I won't be able to do this for a while because I am in the middle of moving. The external drive has been disconnected and packed. Perhaps in a week or so I'll be able to do this. 

Thank you.

---

