---
title: "Drive mounts as Partition, without UUID (only PARTUUID)"
date: 2016-04-08
forum: General Help
---

### Post by andre46 on 2016-04-08
As of my most recent updates, one of my 7 external drives is now mounting as a Partition only, and not as a full drive.  Maybe I'm mis-explaining the issue, but this is leading to the drive not getting caught by FSTAB, and I can't find a way to access the drive.

/dev/sdc1 is the issue:
```
andre@NAS:~$ sudo blkid
[sudo] password for andre: 
/dev/sda1: UUID="51AB-2663" TYPE="vfat" PARTUUID="c712dc64-a7d7-4ad3-a5dc-e07490a705d3"
/dev/sda2: UUID="e1abd730-7d20-4120-90d2-d71282a96d87" TYPE="ext4" PARTUUID="50cfa454-3cf7-4182-a210-e2fe1882ba4f"
/dev/sda3: UUID="412337ba-019b-45a7-8376-2a9236201a2e" TYPE="swap" PARTUUID="6385f4ee-8cd8-4540-9fb7-62587471f4d4"
/dev/sdb1: LABEL="4TB_2" UUID="affca0f6-7ae8-45f5-9e59-92170c3c437a" TYPE="ext4" PARTUUID="7ed95559-df56-4ae3-84b3-ffb9f98a4db0"
/dev/sdc1: PARTUUID="d2a98f7e-1857-474b-9973-b2676d2302f0"
/dev/sdd1: LABEL="2TB_2" UUID="deb41754-7157-42f0-8129-d1545f10ace4" TYPE="ext4" PARTUUID="7acc80f1-01"
/dev/sde1: LABEL="5TB_1" UUID="c9fd552c-921c-4ddb-bb46-fe557943d311" TYPE="ext4" PARTUUID="3bed9e0c-b45e-4518-9af5-eadcd3a97cc1"
/dev/sdf1: LABEL="4TB_1" UUID="f90279d3-7127-4fdb-845c-7c7f60fd6eec" TYPE="ext4" PARTUUID="4a9a71ca-7c1e-42a0-865e-199de4f8b47c"
/dev/sdg1: LABEL="5TB_2" UUID="2b1fcea7-8183-43d4-8a1a-43c54d9e8e5d" TYPE="ext4"
/dev/sdh1: LABEL="2TB" UUID="f238352a-805e-40e8-a676-c62f0b6b0acb" TYPE="ext4" PARTUUID="5b349937-b657-4c5a-a4e1-1f8eaad3382c"

```
And here is my FSTAB file (the drive should be 4TB_3:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=e1abd730-7d20-4120-90d2-d71282a96d87 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=51AB-2663  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=412337ba-019b-45a7-8376-2a9236201a2e none            swap    sw              0       0
#
#
#
#### MOUNT POINTS ####
# 2TB_1
UUID=f238352a-805e-40e8-a676-c62f0b6b0acb  /mnt/2TB_1   ext4 defaults,nobootwait,noatime 0 2
# 2TB_2
UUID=deb41754-7157-42f0-8129-d1545f10ace4  /mnt/2TB_2   ext4 defaults,nobootwait,noatime 0 2
# 4TB_1
UUID=f90279d3-7127-4fdb-845c-7c7f60fd6eec  /mnt/4TB_1   ext4 defaults,nobootwait,noatime 0 2
# 4TB_2
UUID=affca0f6-7ae8-45f5-9e59-92170c3c437a  /mnt/4TB_2   ext4 defaults,nobootwait,noatime 0 2
# 4TB_3
UUID=3b7c225a-2602-4224-8a80-dc59d13cc1a4  /mnt/4TB_3   ext4 defaults,nobootwait,noatime 0 2
# 5TB_1
UUID=c9fd552c-921c-4ddb-bb46-fe557943d311  /mnt/5TB_1   ext4 defaults,nobootwait,noatime 0 2
# 5TB_2
UUID=2b1fcea7-8183-43d4-8a1a-43c54d9e8e5d  /mnt/5TB_2   ext4 defaults,nobootwait,noatime 0 2
#

```


I do recall lubuntu performing a filesystem check on a drive during a recent reboot, but it didn't throw any errors at me.

I'm having other issues with the system booting (I usually need to boot the system from GRUB using an UPSTART kernel - the splash screen always seems to freeze).  Also, I have way more kernels installed than I think I'm supposed to - I believe the system is only suppsed to hold on to a few, and I have 6 or 7 kernels still installed.

My top concern is getting the drive working again, but just trying to provide information.

---

### Post by bab1 on 2016-04-08
> **andre46 said:**
> As of my most recent updates, one of my 7 external drives is now mounting as a Partition only, and not as a full drive.  Maybe I'm mis-explaining the issue, but this is leading to the drive not getting caught by FSTAB, and I can't find a way to access the drive.

/dev/sdc1 is the issue:
```
andre@NAS:~$ sudo blkid
[sudo] password for andre: 
/dev/sda1: UUID="51AB-2663" TYPE="vfat" PARTUUID="c712dc64-a7d7-4ad3-a5dc-e07490a705d3"
/dev/sda2: UUID="e1abd730-7d20-4120-90d2-d71282a96d87" TYPE="ext4" PARTUUID="50cfa454-3cf7-4182-a210-e2fe1882ba4f"
/dev/sda3: UUID="412337ba-019b-45a7-8376-2a9236201a2e" TYPE="swap" PARTUUID="6385f4ee-8cd8-4540-9fb7-62587471f4d4"
/dev/sdb1: LABEL="4TB_2" UUID="affca0f6-7ae8-45f5-9e59-92170c3c437a" TYPE="ext4" PARTUUID="7ed95559-df56-4ae3-84b3-ffb9f98a4db0"
/dev/sdc1: PARTUUID="d2a98f7e-1857-474b-9973-b2676d2302f0"
/dev/sdd1: LABEL="2TB_2" UUID="deb41754-7157-42f0-8129-d1545f10ace4" TYPE="ext4" PARTUUID="7acc80f1-01"
/dev/sde1: LABEL="5TB_1" UUID="c9fd552c-921c-4ddb-bb46-fe557943d311" TYPE="ext4" PARTUUID="3bed9e0c-b45e-4518-9af5-eadcd3a97cc1"
/dev/sdf1: LABEL="4TB_1" UUID="f90279d3-7127-4fdb-845c-7c7f60fd6eec" TYPE="ext4" PARTUUID="4a9a71ca-7c1e-42a0-865e-199de4f8b47c"
/dev/sdg1: LABEL="5TB_2" UUID="2b1fcea7-8183-43d4-8a1a-43c54d9e8e5d" TYPE="ext4"
/dev/sdh1: LABEL="2TB" UUID="f238352a-805e-40e8-a676-c62f0b6b0acb" TYPE="ext4" PARTUUID="5b349937-b657-4c5a-a4e1-1f8eaad3382c"

```
And here is my FSTAB file (the drive should be 4TB_3:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=e1abd730-7d20-4120-90d2-d71282a96d87 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=51AB-2663  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=412337ba-019b-45a7-8376-2a9236201a2e none            swap    sw              0       0
#
#
#
#### MOUNT POINTS ####
# 2TB_1
UUID=f238352a-805e-40e8-a676-c62f0b6b0acb  /mnt/2TB_1   ext4 defaults,nobootwait,noatime 0 2
# 2TB_2
UUID=deb41754-7157-42f0-8129-d1545f10ace4  /mnt/2TB_2   ext4 defaults,nobootwait,noatime 0 2
# 4TB_1
UUID=f90279d3-7127-4fdb-845c-7c7f60fd6eec  /mnt/4TB_1   ext4 defaults,nobootwait,noatime 0 2
# 4TB_2
UUID=affca0f6-7ae8-45f5-9e59-92170c3c437a  /mnt/4TB_2   ext4 defaults,nobootwait,noatime 0 2
# 4TB_3
UUID=3b7c225a-2602-4224-8a80-dc59d13cc1a4  /mnt/4TB_3   ext4 defaults,nobootwait,noatime 0 2
# 5TB_1
UUID=c9fd552c-921c-4ddb-bb46-fe557943d311  /mnt/5TB_1   ext4 defaults,nobootwait,noatime 0 2
# 5TB_2
UUID=2b1fcea7-8183-43d4-8a1a-43c54d9e8e5d  /mnt/5TB_2   ext4 defaults,nobootwait,noatime 0 2
#

```


I do recall lubuntu performing a filesystem check on a drive during a recent reboot, but it didn't throw any errors at me.

I'm having other issues with the system booting (I usually need to boot the system from GRUB using an UPSTART kernel - the splash screen always seems to freeze).  Also, I have way more kernels installed than I think I'm supposed to - I believe the system is only suppsed to hold on to a few, and I have 6 or 7 kernels still installed.

My top concern is getting the drive working again, but just trying to provide information.
Let's see a more definitive list.  Post the output of this command```
sudo blkid -c /dev/null -o list
```...this will show more info on all the mounted partitions.

There terms are a little different than what Windows uses.  The Windows drive is a Linux partition.  You mount file systems on partitions with fstab.  The Linux term, "drive", is the physical device (the HDD).  The UUID is for the partition and is created when the partition is formatted with a file system.

---

### Post by andre46 on 2016-04-08
```

device     fs_type label    mount point    UUID-------------------------------------------------------------------------------
/dev/sda1  vfat             /boot/efi      51AB-2663
/dev/sda2  ext4             /              e1abd730-7d20-4120-90d2-d71282a96d87
/dev/sda3  swap             <swap>         412337ba-019b-45a7-8376-2a9236201a2e
/dev/sdb1  ext4    4TB_2    /mnt/4TB_2     affca0f6-7ae8-45f5-9e59-92170c3c437a
/dev/sdc1                   (not mounted)  
/dev/sdd1  ext4    2TB_2    /mnt/2TB_2     deb41754-7157-42f0-8129-d1545f10ace4
/dev/sde1  ext4    5TB_1    /mnt/5TB_1     c9fd552c-921c-4ddb-bb46-fe557943d311
/dev/sdf1  ext4    4TB_1    /mnt/4TB_1     f90279d3-7127-4fdb-845c-7c7f60fd6eec
/dev/sdg1  ext4    5TB_2    /mnt/5TB_2     2b1fcea7-8183-43d4-8a1a-43c54d9e8e5d
/dev/sdh1  ext4    2TB      /mnt/2TB_1     f238352a-805e-40e8-a676-c62f0b6b0acb
```

alright -  so here it's showing as not mounted.  For some reason, mounting it within the Disks app isn't an option.  What say you?

---

### Post by oldfred on 2016-04-08
Post this:
 sudo parted /dev/sdc unit s print 

It looks like you may not have partitioned drive, just formatted it? Above will show partitions, if you have any.

---

### Post by andre46 on 2016-04-08
I suppose anything is possible, but I've been using this drive for months without issue.  Nothing with this drive changed recently in order to cause this, and there is a large amount of data on it that I'm just crossing my fingers is unaffected.

```

andre@NAS:~$ sudo parted /dev/sdc unit s print
[sudo] password for andre: 
Model: ST4000NM 0033-9ZM170 (scsi)
Disk /dev/sdc: 7814037168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start  End          Size         File system  Name  Flags
 1      2048s  7814037134s  7814035087s


```

---

### Post by bab1 on 2016-04-09
> **andre46 said:**
> I suppose anything is possible, but I've been using this drive for months without issue.  Nothing with this drive changed recently in order to cause this, and there is a large amount of data on it that I'm just crossing my fingers is unaffected.

```

andre@NAS:~$ sudo parted /dev/sdc unit s print
[sudo] password for andre: 
Model: ST4000NM 0033-9ZM170 (scsi)
Disk /dev/sdc: 7814037168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start  End          Size         File system  Name  Flags
 1      2048s  7814037134s  7814035087s


```
As @oldfred has suggested, it appears that this partition (sdc1) on the device /dev/sdc has lost its formatting.  What I would try is this command```
sudo fsck /dev/sdc1
```...this is the Linux file system checker.  It may just repair the partition or it my tell you more about what is wrong.  Post any errors back here.

Here is a tutorial on fsck: [http://www.thegeekstuff.com/2012/08/fsck-command-examples/]("http://www.thegeekstuff.com/2012/08/fsck-command-examples/")

[COLOR="#0000FF"]Edit: This kind of this does happen.  I have backups of all my data for just this scenario.  If that is the case you should check the integrity of the device with SMART tools (smartmon) before putting the device back in service (reformatting it).[/COLOR]

---

### Post by andre46 on 2016-04-09
```

andre@NAS:~$ sudo fsck /dev/sdc1
[sudo] password for andre: 
fsck from util-linux 2.25.2
e2fsck 1.42.12 (29-Aug-2014)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
4TB_3 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  +(512000000--512001024) +(550731776--550732800) +(644972544--644973568)
Fix<y>? 

```
Should I fix?

---

### Post by oldfred on 2016-04-09
It looks like you had an issue with drive. Did you have power failure or just shut off computer?
> 4TB_3 was not cleanly unmounted, check forced.

You may get hundreds of requests for yes/no.

I often suggest this which uses e2fsck twice.
From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdc1 to your partition(s)
 #e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdc1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdc1

---

### Post by andre46 on 2016-04-09
I had a power outage a couple days ago, but I powered everything off before the battery backup ran out.  I had a previous outage a few weeks ago, where I was not so lucky - however this issue just came up now.

I don't have a live dvd or flash that i can use at the moment, so I'll just power down and disconnect all other drives.  I don't have the time to run these commands at the moment - I'll run them Monday evening and report back.  Thanks so much for your help thus far.

---

### Post by bab1 on 2016-04-09
> **andre46 said:**
> ```

andre@NAS:~$ sudo fsck /dev/sdc1
[sudo] password for andre: 
fsck from util-linux 2.25.2
e2fsck 1.42.12 (29-Aug-2014)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
4TB_3 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  +(512000000--512001024) +(550731776--550732800) +(644972544--644973568)
Fix<y>? 

```
Should I fix?
I think you should follow @oldfred's advice.  I also think this is more than just a power cut induced non-clean unmount of the partition (sdc1).  This goes back to your problems that you posted about in January: [http://ubuntuforums.org/showthread.php?t=2308510]("http://ubuntuforums.org/showthread.php?t=2308510").  

My guess is this shutdown unmount problem is most likely  induced by your complex /etc/fstab configuration.  It may be that the configuration causes a timing situation that the OS can't handle correctly.  If you unmount a partition that also has a bind mount you can have these kinds of problems.

You might think about asking the forum mods to combine this thread with the original discussion on this subject as it really is a continuation of that thread.  Just click on the "report abuse" icon at the lower left and make your request.

---

### Post by andre46 on 2016-04-11
Had a bit of trouble running that first command:
```

andre@NAS:~$ sudo e2fsck -C0 -p -f -v /dev/sdc1
[sudo] password for andre: 
e2fsck: Bad magic number in super-block while trying to open /dev/sdc1
/dev/sdc1: 
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

```

So I didn't run the 2nd one.  Just leaving it idle for now.

I don't know that I'd consider my fstab file to be *complex.* In fact, here it is in it's entirety:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=e1abd730-7d20-4120-90d2-d71282a96d87 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=51AB-2663  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=412337ba-019b-45a7-8376-2a9236201a2e none            swap    sw              0       0
#
#
#
#### MOUNT POINTS ####
# 2TB_1
UUID=f238352a-805e-40e8-a676-c62f0b6b0acb  /mnt/2TB_1   ext4 defaults,nobootwait,noatime 0 2
# 2TB_2
UUID=deb41754-7157-42f0-8129-d1545f10ace4  /mnt/2TB_2   ext4 defaults,nobootwait,noatime 0 2
# 4TB_1
UUID=f90279d3-7127-4fdb-845c-7c7f60fd6eec  /mnt/4TB_1   ext4 defaults,nobootwait,noatime 0 2
# 4TB_2
UUID=affca0f6-7ae8-45f5-9e59-92170c3c437a  /mnt/4TB_2   ext4 defaults,nobootwait,noatime 0 2
# 4TB_3
UUID=3b7c225a-2602-4224-8a80-dc59d13cc1a4  /mnt/4TB_3   ext4 defaults,nobootwait,noatime 0 2
# 5TB_1
UUID=c9fd552c-921c-4ddb-bb46-fe557943d311  /mnt/5TB_1   ext4 defaults,nobootwait,noatime 0 2
# 5TB_2
UUID=2b1fcea7-8183-43d4-8a1a-43c54d9e8e5d  /mnt/5TB_2   ext4 defaults,nobootwait,noatime 0 2
#
#### BINDS ####
/mnt/2TB_2/Work                        /mnt/2TB_1/Work                              none bind 0 0
# FTP SHARE FOLDER
/mnt/4TB_1/Movies\040(New)             /home/andre/FTP-Share/Movies_New             none bind 0 0
/mnt/4TB_1/Movies\040Archive           /home/andre/FTP-Share/Movies_Archive/#-J     none bind 0 0
/mnt/4TB_3/Movies\040Archive\040(K-Z)  /home/andre/FTP-Share/Movies_Archive/K-Z     none bind 0 0
/mnt/2TB_1/Completed/TV/               /home/andre/FTP-Share/TV_New                 none bind 0 0
/mnt/4TB_2/TV_Archive_#-F              /home/andre/FTP-Share/TV_Archive/#-F         none bind 0 0
/mnt/5TB_1/TV_Archive_G-R              /home/andre/FTP-Share/TV_Archive/G-R         none bind 0 0
/mnt/5TB_2/TV_Archive_S-Z              /home/andre/FTP-Share/TV_Archive/S-Z         none bind 0 0
/mnt/2TB_2/Upload                      /home/andre/FTP-Share/Upload                 none bind 0 0
# FTP READ ONLY FOLDER
/mnt/4TB_1/Movies\040(New)             /home/andre/FTP-ReadOnly/Movies_New          none bind 0 0
/mnt/4TB_1/Movies\040Archive           /home/andre/FTP-ReadOnly/Movies_Archive/#-J  none bind 0 0
/mnt/4TB_3/Movies\040Archive\040(K-Z)  /home/andre/FTP-ReadOnly/Movies_Archive/K-Z  none bind 0 0
/mnt/2TB_1/Completed/TV/               /home/andre/FTP-ReadOnly/TV_New              none bind 0 0
/mnt/4TB_2/TV_Archive_#-F              /home/andre/FTP-ReadOnly/TV_Archive/#-F      none bind 0 0
/mnt/5TB_1/TV_Archive_G-R              /home/andre/FTP-ReadOnly/TV_Archive/G-R      none bind 0 0
/mnt/5TB_2/TV_Archive_S-Z              /home/andre/FTP-ReadOnly/TV_Archive/S-Z      none bind 0 0
/mnt/2TB_1/Marcus/                     /home/andre/FTP-ReadOnly/Marcus              none bind 0 0

```

The binds are just for FTP usage.  But I swear I didn't unmount anything the other day... I get what you're saying about a possible timing issue, but who knows...

---

### Post by bab1 on 2016-04-11
> **andre46 said:**
> ...

I don't know that I'd consider my fstab file to be *complex.* In fact, here it is in it's entirety:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=e1abd730-7d20-4120-90d2-d71282a96d87 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=51AB-2663  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=412337ba-019b-45a7-8376-2a9236201a2e none            swap    sw              0       0
#
#
#
#### MOUNT POINTS ####
# 2TB_1
UUID=f238352a-805e-40e8-a676-c62f0b6b0acb  /mnt/2TB_1   ext4 defaults,nobootwait,noatime 0 2
# 2TB_2
UUID=deb41754-7157-42f0-8129-d1545f10ace4  /mnt/2TB_2   ext4 defaults,nobootwait,noatime 0 2
# 4TB_1
UUID=f90279d3-7127-4fdb-845c-7c7f60fd6eec  /mnt/4TB_1   ext4 defaults,nobootwait,noatime 0 2
# 4TB_2
UUID=affca0f6-7ae8-45f5-9e59-92170c3c437a  /mnt/4TB_2   ext4 defaults,nobootwait,noatime 0 2
# 4TB_3
UUID=3b7c225a-2602-4224-8a80-dc59d13cc1a4  /mnt/4TB_3   ext4 defaults,nobootwait,noatime 0 2
# 5TB_1
UUID=c9fd552c-921c-4ddb-bb46-fe557943d311  /mnt/5TB_1   ext4 defaults,nobootwait,noatime 0 2
# 5TB_2
UUID=2b1fcea7-8183-43d4-8a1a-43c54d9e8e5d  /mnt/5TB_2   ext4 defaults,nobootwait,noatime 0 2
#
#### BINDS ####
/mnt/2TB_2/Work                        /mnt/2TB_1/Work                              none bind 0 0
# FTP SHARE FOLDER
/mnt/4TB_1/Movies\040(New)             /home/andre/FTP-Share/Movies_New             none bind 0 0
/mnt/4TB_1/Movies\040Archive           /home/andre/FTP-Share/Movies_Archive/#-J     none bind 0 0
/mnt/4TB_3/Movies\040Archive\040(K-Z)  /home/andre/FTP-Share/Movies_Archive/K-Z     none bind 0 0
/mnt/2TB_1/Completed/TV/               /home/andre/FTP-Share/TV_New                 none bind 0 0
/mnt/4TB_2/TV_Archive_#-F              /home/andre/FTP-Share/TV_Archive/#-F         none bind 0 0
/mnt/5TB_1/TV_Archive_G-R              /home/andre/FTP-Share/TV_Archive/G-R         none bind 0 0
/mnt/5TB_2/TV_Archive_S-Z              /home/andre/FTP-Share/TV_Archive/S-Z         none bind 0 0
/mnt/2TB_2/Upload                      /home/andre/FTP-Share/Upload                 none bind 0 0
# FTP READ ONLY FOLDER
/mnt/4TB_1/Movies\040(New)             /home/andre/FTP-ReadOnly/Movies_New          none bind 0 0
/mnt/4TB_1/Movies\040Archive           /home/andre/FTP-ReadOnly/Movies_Archive/#-J  none bind 0 0
/mnt/4TB_3/Movies\040Archive\040(K-Z)  /home/andre/FTP-ReadOnly/Movies_Archive/K-Z  none bind 0 0
/mnt/2TB_1/Completed/TV/               /home/andre/FTP-ReadOnly/TV_New              none bind 0 0
/mnt/4TB_2/TV_Archive_#-F              /home/andre/FTP-ReadOnly/TV_Archive/#-F      none bind 0 0
/mnt/5TB_1/TV_Archive_G-R              /home/andre/FTP-ReadOnly/TV_Archive/G-R      none bind 0 0
/mnt/5TB_2/TV_Archive_S-Z              /home/andre/FTP-ReadOnly/TV_Archive/S-Z      none bind 0 0
/mnt/2TB_1/Marcus/                     /home/andre/FTP-ReadOnly/Marcus              none bind 0 0

```

The binds are just for FTP usage.  But I swear I didn't unmount anything the other day... I get what you're saying about a possible timing issue, but who knows...
It is a complex configuration.  Your problem was been well documented previously.  The very same warnings in the logs that you are getting now show up in those previous posts.  There is no getting around proper diagnosing of the problem.  In my book that means commenting out the bind mounts for the foreseeable future.

As far as finding the alternative superblocks you can [**follow this**]("http://www.cyberciti.biz/faq/linux-find-alternative-superblocks/") to see how to find them.  Why would you not run fsck agains the alternatives?  My guess is that the partition is damaged beyond repair.  So what have you to loose?  Check the HDD SMART info, and if the device is good, reformat the partition and restore your backed up data.

---

### Post by andre46 on 2016-04-12
ok - actually... looks like this is good news.  I ran 
[COLOR=#333333]```
sudo mke2fs -n /dev/sdc1
```
to find where the backup superblocks are, and then ran this[/COLOR]
```

andre@NAS:~$ sudo e2fsck -b 32768 -C0 -p -f -v /dev/sdc1
[sudo] password for andre: 
                                                                               
        2967 inodes used (0.00%, out of 244195328)
           9 non-contiguous files (0.3%)
           2 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 2679/280
   407817447 blocks used (41.75%, out of 976754385)
           0 bad blocks
         230 large files


        2667 regular files
         291 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
           0 symbolic links (0 fast symbolic links)
           0 sockets
------------
        2958 files

```

Drive appears to be fine and mounted now.  Files seem to work - looks as though nothing happened in the first place.  I'm going to leave the device idle for now so I can heed your advice - maybe there is something else you want to check before I decide "everything is fixed"

I get your point about the fstab file... my current short-term plan is to comment out the bind point lines from the fstab, power the system down, reconnect all drives, and then power on again.  I believe that will get me fully back online for now.  As for long-term, I think I want to proceed in a different way than you are anticipating.  Right now - I'm heavily considering a clean OS install, and possibly even changing to Ubuntu Mate.  I have other issues with this system, and I feel as though a clean install may be the best way to attack all issues at once.  It'll be a pain - and I'm sure I'll make a new post in the near future in order to get a better grasp on how I can do it efficiently... but it feels like it may be a necessity.

I believe you see what I'm doing with the bind mounts... It's just to make multiple drives available for FTP usage.  Is there any other way to achieve this end result?  Symlinks? Maybe just a startup script that does the bind mounts (rather than within the fstab file)?  Anything?

Thanks again for your help.

---

### Post by andre46 on 2016-04-12
welp - I decided everything was fixed.  Followed my short term plan, and everything went perfectly.  Startup was a breeze, too... which has been an issue since the fstab changes.  So at the moment, it does feel likely that fstab was the cause of my boot issues.

I guess I'd like some help with the last bit I mentioned in my last post - what can I use beside bind mounts within the fstab file to achieve a better, more stable result?  Thanks!

---

### Post by bab1 on 2016-04-13
> **andre46 said:**
> ...

I believe you see what I'm doing with the bind mounts... It's just to make multiple drives available for FTP usage.  Is there any other way to achieve this end result?  Symlinks? Maybe just a startup script that does the bind mounts (rather than within the fstab file)?

> welp - I decided everything was fixed. Followed my short term plan, and everything went perfectly. Startup was a breeze, too... which has been an issue since the fstab changes. So at the moment, it does feel likely that fstab was the cause of my boot issues.

I guess I'd like some help with the last bit I mentioned in my last post - what can I use beside bind mounts within the fstab file to achieve a better, more stable result? 
What exactly does this mean; "It's just to make multiple drives available for FTP usage"?  Hopefully you are not using basic FTP to begin with anyway.  How are you using FTP?  What application are you using for this?  Could it be that you are having trouble accessing the file and directories on these partitions at their mount points (e.g. /mnt/<mount-point>/<some-directory>)?

At this point I don't see any need at all for the bind mounts you have been using.  What problem were you having that caused you to try using that type of mount?  Could it have been file and directory access permissions? So far, there is no indication that some configuration parameter in the  fstab file will help your situation.

---

### Post by andre46 on 2016-04-13
I'm using SFTP, not plain old FTP.  The bind mounts were so that I can share aspects of drives.  From what I know of FTP - you set a single home directory for each account.  I need specific portions of all the drives to be accessible through this home directory.  I do not want to provide access to the roots of each, so I don't want the FTP directory to be the /mnt/ folder.  The bind mounts existed so that I could put aspects of each drive in specific subfolders of this home directory.  If there is a better way, I really would like to know.

I configured SFTP with gadmin proftpd, google, and some help from their forum

---

### Post by bab1 on 2016-04-13
> **andre46 said:**
> I'm using SFTP, not plain old FTP.  The bind mounts were so that I can share aspects of drives.  From what I know of FTP - you set a single home directory for each account.  I need specific portions of all the drives to be accessible through this home directory.  I do not want to provide access to the roots of each, so I don't want the FTP directory to be the /mnt/ folder.  The bind mounts existed so that I could put aspects of each drive in specific subfolders of this home directory.  If there is a better way, I really would like to know.

I configured SFTP with gadmin proftpd, google, and some help from their forum
The answer is either you rearrange the file structure for simple access to the data by the user or you restrict access via user and group permissions to parts of the data store.  The issue does not appear to be a mount (bind) issue.  It looks to be an access (ownership/permissions) issue to me.

I don't use any GUI tools (gadmin).  In fact I urge you to purge the system of gadmin.  It's more trouble than it is worth.

Proftpd is not SFTP.  It is FTPS.  A completely different thing.  I would use the SSH (SFTP) instead.  The config file is simple and well documented.  Each user can have a separate ChrootDirectory.  That along with a simple file structure should take care of all your needs.

Can you show an example of what (why) you are using what you have now?

---

