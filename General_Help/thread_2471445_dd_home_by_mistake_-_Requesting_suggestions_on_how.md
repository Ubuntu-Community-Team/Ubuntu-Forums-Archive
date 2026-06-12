---
title: "dd /home by mistake - Requesting suggestions on how to recover files..."
date: 2022-01-30
forum: General Help
---

### Post by k3nden on 2022-01-30
I had 2 disk setup running 18.04. A 120GB SSD for / and [SWAP] and a 1TB  for /home. I rebooted today and /home is now gone and I can only boot to emergency mode. LSBLK reports the drive as 931GB with two partitions of 790M and 74M. I can only mount the 790M which looks a lot like an Arch boot partition. I suspect that I pointed dd to the wrong output device sometime in the past and when I rebooted the changes were written.  I realize that I have overwritten the beginning of this disk but was hoping for recommendations on how to recover the most of files from it? google searches have suggested Testdisk and Revuca and steps to recover root/efi partitions. As this is the /home drive I am not really sure how best to proceed. 

  Journal output tells me** 5b7832d9-4e48-4ab4-b24d-9b7513e8d2f7** is lost...FSTAB sort of says the same.



[HTML]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during installation
UUID=07f24f3b-59bd-4e1c-b1d8-dee50dd0936f /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb1 during installation
UUID=2DEA-5743  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sdc1 during installation
# this disk is gone UUID=c3070f66-363c-4a8f-a29f-050e700f63bf /mnt/home           ext4    defaults        0       2
# this is the small intel disk : UUID=83cc27d7-28ad-4db1-a513-9f46bd16069d /home           ext4    defaults        0       2
UUID=5b7832d9-4e48-4ab4-b24d-9b7513e8d2f7 /home           ext4    defaults        0       2

# swap was on /dev/sdb3 during installation
UUID=892f1fd2-170d-4a79-8429-505884e4ae1b none            swap    sw              0       0
LABEL=Seagate\040Backup\040Plus\040Drive /media/Seagate auto nosuid,nodev,nofail,noauto,x-gvfs-show 0 0
[/HTML]

---

### Post by HermanAB on 2022-01-30
The best and fastest way to recover is to reinstall and restore your data from a backup.

Otherwise, you can try testdisk, but don't expect too much, since all the filenames will be lost.

---

### Post by dragonfly41 on 2022-01-31
I am guessing that you have no backups.
If you are to attempt recovery of /home you must prepare first.

First, you will need a LiveUSB with testdisk installed on that.

Testdisk is applied to unmounted drives.

Second you will need another 1TB drive formatted into which any recovered files will be saved. This point is often overlooked since you cannot save files into the drive you are attempting to recover. However you can familiarise yourself with testdisk options before taking the decision about purchasing extra drive(s). Just do not *save* at this point into drive under test.

dd is a destroyer.

Another thing you might try is install R-Linux on your LiveUSB and see if you can recover.

Finally depending on the value of content in /home some advise cloning the drive and then applying recovery methods to the clone (the original being locked away). This would require yet another 1 TB drive. So it can be expensive.

[P.S.] When exploring if R-Linux might help, launch R-Linux and in toolbar read Help > Help > Data Recovery Using R-Linux.

And lastly if you install Gparted into LiveUSB you can inspect partitions. There is a feature Device > Attempt Data Rescue but I have never used that.

---

### Post by oldfred on 2022-01-31
Were you using gpt partitioning?
sudo gdisk -l /dev/sdc

dd would not know about backup partition table at end of drive.
But all data at beginning of drive was totally overwritten.
If backup can be restored you also need fsck and maybe other repairs.

---

### Post by k3nden on 2022-01-31
Thanks I have  installed rlinux- I have much to learn to be able to use it...cloning the drive seems to be a good idea.

---

### Post by k3nden on 2022-01-31
Drangonfly41 - Thanks I have  installed rlinux- I have much to learn to be able to use it. I had not considered cloning the drive(more dd)

Oldfred - the gdisk -l /dev/sdc   found valid MBR and GPT.
Is there a partition table at the end of the drive that gdisk can access and possibly repair/recover? It would be fun to see how much of this drive I can recover.

---

### Post by oldfred on 2022-01-31
If you reinstalled, then no.
Gdisk finds backup partition table and dd should have only overwritten primary partition table at beginning of drive.
But reinstall should also then create new primary & backup partition tables, so now nothing of old structure exists in partition tables.
Testdisk may have found old data with deeper search, with full file names for some data.

And photorec can find left over files, but not full file names. I have used photorec and learned to do better backups. It took overnight on a smaller drive and weeks to compare files to old backup. For text files it also found very old deleted files, so had multiple copies of same file and difficult to tell old file, backup file & various other versions.

---

### Post by dragonfly41 on 2022-01-31
I had forgotten this link which might help.

[Data Recovery]("https://help.ubuntu.com/community/DataRecovery")

---

### Post by k3nden on 2022-01-31
I have not reinstalled anything. I ordered a disk that i hope to clone sdc and have been reading about repairing gpt disks. Gdisk does think it is damaged.


```
Found valid MBR and GPT. Which do you want to use?
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: 2
Using GPT and creating fresh protective MBR.
Disk /dev/sdc: 1953525168 sectors, 931.5 GiB
Model: WDC  WDS100T2B0A
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 32323032-3130-4130-B130-303031313036
Partition table holds up to 248 entries
Main partition table begins at sector 2 and ends at sector 63
First usable sector is 64, last usable sector is 1770072
Partitions will be aligned on 64-sector boundaries
Total free space is 601 sectors (300.5 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              64         1617919   790.0 MiB   0700  ISOHybrid
   2         1617920         1769471   74.0 MiB    0700  ISOHybrid1
```

---

### Post by oldfred on 2022-01-31
Gdisk is only finding the dd'd ISO.
Does not look like it has the backup gpt with original data.
If you knew exact sectors of original partition(s), you can recreate those. Or maybe testdisk will find old partition and let you restore it.
If testdisk works & you can drill down to see files immediately copy those to another device. Some have seen those files, but never were able to get them after closing testdisk.

---

### Post by dragonfly41 on 2022-01-31
You can always use your newly purchased drive after this recovery exerciae .. for future backups.

Meanwhile investigate also [ddrescue ]("https://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html")features running on LiveUSB,

You will find sample discussions if you search. [This one]("https://askubuntu.com/questions/1107079/using-ddrescue-to-recover-hard-drive-dont-know-if-image-is-being-created") made the mistake I referred to earlier .. overwriting the very same drive.
So it is a necessary move to have a second drive .. which you are now purchasing.

---

### Post by TheFu on 2022-01-31
Good advice above.  

Long ago, I lost 80% of my data. Even that didn't get me backup religion, but a few years after that loss, my home server got hacked and I happened to have a backup from 1 week earlier which completely saved my machine and data and sanity.  I got backup religion from that.
Having daily, versioned, backups is pretty easy. For home users, even weekly, versioned, backups would make a huge difference in the ability to recover.
I split my data into 3 groups.
[LIST=1]
[*]Stuff that can change multiple times a day, need full versioned backups of this.
[*]Stuff that seldom changes AND is huge - mostly media files.
[*]Stuff not to backup; don't need, but nice to have.
[/LIST]
Things in /home (or where ever the HOME directories are) are in the first group. Same for system settings (/etc/) and lists of installed packages. I want daily, versioned, automatic, backups of these things.  This turns into about 5-10GB per system and 120-180 days of versioned backups uses about 1.3x the original storage amount.  So, if I have 10GB of data to backup, 120days worth that is versioned would be about 13GB.  Is that not a bargain?  Why wouldn't people create versioned backups if that was the storage needed?

Media files are kept on 1 system with lots of storage. No RAID and it doesn't get versioned backups, just a delayed mirror via rsync.  For 20TB of main data, that means 20TB for backups

On most my laptops, I have some scratch storage mounted separately. This is for stuff that lives on a different computer - usually media - that I only want copies of when traveling.  I put it into /stuff/ and it doesn't get backed up and I really don't care if it gets wiped. Those files are for travel convenience only.

Oh, and I keep the "backup disk" separate from every other sort of data. It is only used for backups, not thing else.
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       1.4T  1.3T   32G  98% /Backups
```
That 1.5TB drive has backups for a bunch of systems, many have been retired or sold for years. About half are from 2008-2015, so the fact that it seems really full just means I'm using it as archival for dead systems that don't exist anywhere else anymore. 

Anyway, being able to restore from backups is 10,000x easier than every other method.

---

### Post by Tadaen_Sylvermane on 2022-02-01
I finally found my backup religion after having to download 70+gb on a 20mb isp a few times. Created a few scripts. At any given time I've got 2 different types of backups of damn near everything.

For simple large data backup (steam games and the like) [https://gitlab.com/jmgibson1981/homescripts/-/blob/master/shell/rsyncbackup.sh](https://gitlab.com/jmgibson1981/homescripts/-/blob/master/shell/rsyncbackup.sh)
This one covers everything else [https://gitlab.com/jmgibson1981/homescripts/-/blob/master/shell/homebackups.sh](https://gitlab.com/jmgibson1981/homescripts/-/blob/master/shell/homebackups.sh)

For Windows I've been using Duplicati + a bi-weekly clonezilla run. Much prefer the automated LVM tar's though.

---

### Post by TheFu on 2022-02-01
> **Tadaen_Sylvermane said:**
> I finally found my backup religion after having to download 70+gb on a 20mb isp a few times. Created a few scripts. At any given time I've got 2 different types of backups of damn near everything.

For simple large data backup (steam games and the like) [https://gitlab.com/jmgibson1981/homescripts/-/blob/master/shell/rsyncbackup.sh](https://gitlab.com/jmgibson1981/homescripts/-/blob/master/shell/rsyncbackup.sh)
This one covers everything else [https://gitlab.com/jmgibson1981/homescripts/-/blob/master/shell/homebackups.sh](https://gitlab.com/jmgibson1981/homescripts/-/blob/master/shell/homebackups.sh)

For Windows I've been using Duplicati + a bi-weekly clonezilla run. Much prefer the automated LVM tar's though.

Good to hear.  I had troubles with duplicity (that's what the script uses) and it uses the 1970s backup schedule unlike modern tools.  Duplicati is a GUI over duplicity, so I bet the backup files are all compatible between Duplicati, DejaDup and duplicity.

Below is THE STANDARD monthly backup schedule:

```
S M T W T F S
- – - – - – - 
M D D D D D F
D D D D D D F
D D D D D D F
D D D D D D F

```
repeat.
[LIST]
[*]    D = Daily differential backup – changed data only, unless you can perform full backups within your backup window without impacting users
[*]    F = Full backups – this limits the number of daily backups to be restored if there is an issue that week to 6 or 7
[*]    M = Monthly – mark the first full backup of each month as the monthly and store it
[*]    If you have limited backup infrastructure, you may need to split the weekly/Full backups between multiple days like Friday, Saturday and Sunday. Since this complicates your overall solution, this should be avoided.
[*]
[/LIST]
This is the SCCS method. SCCS is a software version control tool from long ago that overlays differences onto the original file. Over time, the number of differences to be applied to get to the current file version can become thousands and use lots of processing. RCS is the opposite.  It does reverse-incremental changes. The files are stored in their most recent format and as we want older versions, the diffs are applied.  99% of the time, we want the current version of the file.  0.0001% of the time, we want the version of the file from 2 yrs ago.
Backup tools work in a similar way.
**Duplicity** and tape backups that have full backups weekly/monthly and differences take between the full backups are like SCCS. To restore a file, the restore tool has to find the most recent "full" backup, then apply all the changed forward to the most recent backup.

**Rdiff-backup** works like RCS. The most recent files are stored like an rsync mirror and older versions are stored as diff.gz files over time, and include file metadata changes like the owner, group, ACLs and xattrs.  Duplicity captures all that file metadata too, but the extremely popular rsync+hardlink tools (rsnapshot, back-in-time, and 500 other home-made scripts using the same technique over the last 30+ yrs) only retain the most current file metadata.

Duplicity checks every box on what a backup should be. rdiff-backup lacks built-in encryption and only works over connections that support ssh tunnels or sshfs or NFS. ssh is used by most Unix/Linux network backup tools.  Duplicity does the chunk encryption before transmitting the 5MB backup chunks off the system AND it supports lots and lots of file transfer methods. It is really impressive.

I tried to get the built-in backup tool to work and it did seem to work, but at restore time, it failed.  
For Windows backups, which I haven't booted in a few weeks, I don't store any data on the Windows systems. About every 6 months, I make a clone of my last Windows laptop to a different HDD using ddrescue.  The main Windows install that I use for financial programs runs inside a virtual machine. Again, no data is kept inside that VM, just the OS and about 3 programs. When I done with it, I rsync all the data to a Linux RAID area that also gets backed up to another disk and shut the VM down. Just looked, this is less than 5GB of data total. Each file has a data-stamp in the filename. Once a week, the entire VM image gets copied to a different machine. That's the start and end of my Windows backups. There are 3 files - 2 that are the OS and Data and 1 that is the libvirt VM configuration file.
```
$ du -sh *
35G     Win7Ult-Data2.img
59G     Win7Ult-os.img
4.0K    Win7Ult.xml
```

If I cannot restore from a backup, then any effort creating it is completely useless. Yes, I'm still using an unsupported Win7 OS. It hasn't been patched in years - since the time that MSFT changed the EULA - probably around 2016-ish. I didn't agree with the new terms.

---

