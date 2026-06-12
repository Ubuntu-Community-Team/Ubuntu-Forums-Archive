---
title: "Rsync Stalling on a specific file"
date: 2014-02-25
forum: General Help
---

### Post by Ackis on 2014-02-25
Hello everyone, I'm having an issue with rsync when I try to backup a directory on one of my NASes to an external USB drive.

What happens is that it gets to a specific file and just stalls.  After a while I can't even ctrl-c the process and even kill 9 doesn't stop rsync.

I originally thought that the file might be corrupt or something else was going on with it, but I did the following without any errors:
[LIST]
[*]Renamed the file
[*]Viewed the file (it's an image)
[*]Copy/pasted the file
[*]Deleted the file and pasted on my own hard drive
[/LIST]

If there was something wrong with the file I would have expected viewing it or moving it would have caused an error somewhere but they didn't.

My current status is that I've removed that file and I'm running the rsync command again to see if there's anything else causing issues.  So far there hasn't been.

Once the current rsync is done I was planning on adding the file again and seeing what will happen and eventually I'll want to have this in a cron job.

Edit: It just finished with this error:

I haven't had a chance to google for it yet but I will be, just adding it here in case it's important info.

```

total size is 38522060182  speedup is 1.60
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9]

```

I readded the file and ran the command again only to get this output:

```

sending incremental file list
Hard Drive - Reoverred Data/Pictures/08-August - Science Camp/
Hard Drive - Reoverred Data/Pictures/08-August - Science Camp/08-August - Science Camp 019a.jpg
       32768   1%    0.00kB/s    0:00:00  ^C
rsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at rsync.c(549) [sender=3.0.9]

```

The NAS is a DNS-323 running the alt-f firmware.  There are two 1TB disks inside running in raid 0.

This is the rsync command that I run:

```
sudo rsync -av --progress --delete /backup/DNS-323-backup/John/ /media/USB/backup/John
```

My /etc/fstab/

```

# NAS Shares//192.168.0.102/media   /media/READYNAS/        cifs uid=1500,gid=1005,credentials=/etc/smbcredentials,iocharset=utf8,noserverino,sec=ntlm 0 0
//192.168.0.102/media2  /media/READYNAS2/       cifs uid=1500,gid=1005,credentials=/etc/smbcredentials,iocharset=utf8,noserverino,sec=ntlm 0 0
//192.168.0.100/media   /media/DNS-323/         cifs uid=1500,gid=1005,credentials=/etc/smbcredentials,iocharset=utf8,noserverino,sec=ntlm 0 0


# NAS Backups
//192.168.0.100/backup   /backup/DNS-323-backup/         cifs uid=34,gid=34,credentials=/etc/smbcredentials,iocharset=utf8,noserverino,sec=ntlm 0 0

```

The entry from /var/log/error
/var/log/rsync only has entries a month old, nothing current

```
Feb 25 10:54:14 Ubuntu kernel: [87178.121262] CIFS VFS: SMB response too short (29 bytes)
```

The smb.conf file on the DNS-323:

```

[global]
        workgroup = JOHN
        server string = DNS-323 NAS
        map to guest = Bad User
        passdb backend = smbpasswd
        username map = /etc/samba/smbusers
        syslog only = Yes
        max log size = 32
        enable core files = No
        socket options = IPTOS_LOWDELAY TCP_NODELAY
        hosts allow = 127. 192.168.0.0/255.255.255.0
        print command = lpr -P %p %s; rm %s


[Keys]
        comment = Cryptography Keys
        path = /mnt/md0/John/Keys
        valid users = john
        available = yes
        read only = yes


[John]
        comment = John Files
        path = /mnt/md0/John
        valid users = +users
        available = yes
        read only = no


[Chantelle]
        comment = Chantelle Files
        path = /mnt/md0/Chantelle
        valid users = +users
        available = yes
        read only = no


[Volume_1]
        comment = Volume_1 folder
        path = /mnt/md0
        valid users = +users
        available = yes
        read only = no


[Shared Docs]
        comment = Shared Docs folder
        path = /mnt/md0/Shared Docs
        valid users = +users
        available = yes
        read only = no


[media]
        comment = Media Server folder
        path = /mnt/md0/Shared Docs/Media Server
        valid users = +media
        available = yes
        read only = no


[backup]
        comment = Read Only Backup Share
        path = /mnt/md0
        valid users = +backup
        available = yes
        read only = yes

```

SMART data from the NAS drives:
I know it says there are known issues with the drives, that's part of the reason why I am rsyncing the data to have a backup so I can try to update the drive firmware.

```
smartctl 6.0 2012-10-10 r3643 [armv5tel-linux-2.6.35.14] (local build)Copyright (C) 2002-12, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.11
Device Model:     ST31000333AS
Serial Number:    6TE07KB4
LU WWN Device Id: 5 000c50 00e3c0a34
Firmware Version: SD35
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Sun Feb 23 15:24:58 2014 MST


==> WARNING: There are known problems with these drives,
see the following Seagate web pages:
http://knowledge.seagate.com/articles/en_US/FAQ/207931en
http://knowledge.seagate.com/articles/en_US/FAQ/207951en
http://knowledge.seagate.com/articles/en_US/FAQ/207957en


SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   099   006    Pre-fail  Always       -       199988627
  3 Spin_Up_Time            0x0003   092   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1216
  5 Reallocated_Sector_Ct   0x0033   096   096   036    Pre-fail  Always       -       193
  7 Seek_Error_Rate         0x000f   084   060   030    Pre-fail  Always       -       250948825
  9 Power_On_Hours          0x0032   052   052   000    Old_age   Always       -       42268
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       1
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       61
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   001   001   000    Old_age   Always       -       190
190 Airflow_Temperature_Cel 0x0022   055   045   045    Old_age   Always   In_the_past 45 (Min/Max 43/47)
194 Temperature_Celsius     0x0022   045   055   000    Old_age   Always       -       45 (0 20 0 0 0)
195 Hardware_ECC_Recovered  0x001a   025   025   000    Old_age   Always       -       199988627
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       4
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       4
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%     42259         9240
# 2  Short offline       Completed: read failure       90%     42235         9240
# 3  Short offline       Completed: read failure       90%     42211         9240
# 4  Short offline       Completed: read failure       90%     42187         9240
# 5  Short offline       Completed: read failure       90%     42163         9240
# 6  Short offline       Completed: read failure       90%     42139         9240
# 7  Short offline       Completed: read failure       90%     42115         9240
# 8  Extended offline    Completed: read failure       90%     42091         9240
# 9  Short offline       Completed without error       00%     42067         -
#10  Short offline       Completed without error       00%     42043         -
#11  Short offline       Completed: read failure       90%     42019         36640
#12  Short offline       Completed without error       00%     41995         -
#13  Short offline       Completed without error       00%     41971         -
#14  Short offline       Completed without error       00%     41947         -
#15  Extended offline    Completed without error       00%     41926         -
#16  Short offline       Completed without error       00%     41899         -
#17  Short offline       Completed without error       00%     41875         -
#18  Short offline       Completed without error       00%     41851         -
#19  Short offline       Completed without error       00%     41827         -
#20  Short offline       Completed without error       00%     41803         -
#21  Short offline       Completed without error       00%     41779         -




smartctl 6.0 2012-10-10 r3643 [armv5tel-linux-2.6.35.14] (local build)
Copyright (C) 2002-12, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.11
Device Model:     ST31000333AS
Serial Number:    6TE05CT6
LU WWN Device Id: 5 000c50 0117207ed
Firmware Version: SD35
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Sun Feb 23 15:26:17 2014 MST


==> WARNING: There are known problems with these drives,
see the following Seagate web pages:
http://knowledge.seagate.com/articles/en_US/FAQ/207931en
http://knowledge.seagate.com/articles/en_US/FAQ/207951en
http://knowledge.seagate.com/articles/en_US/FAQ/207957en


SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   099   006    Pre-fail  Always       -       163902185
  3 Spin_Up_Time            0x0003   092   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1205
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       1
  7 Seek_Error_Rate         0x000f   076   060   030    Pre-fail  Always       -       44196219
  9 Power_On_Hours          0x0032   055   055   000    Old_age   Always       -       40105
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       1
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       62
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   005   005   000    Old_age   Always       -       95
190 Airflow_Temperature_Cel 0x0022   056   045   045    Old_age   Always   In_the_past 44 (Min/Max 42/47)
194 Temperature_Celsius     0x0022   044   055   000    Old_age   Always       -       44 (0 20 0 0 0)
195 Hardware_ECC_Recovered  0x001a   027   026   000    Old_age   Always       -       163902185
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     40099         -
# 2  Short offline       Completed without error       00%     40072         -
# 3  Short offline       Completed without error       00%     40048         -
# 4  Short offline       Completed without error       00%     40024         -
# 5  Short offline       Completed without error       00%     40000         -
# 6  Short offline       Completed without error       00%     39976         -
# 7  Short offline       Completed without error       00%     39952         -
# 8  Extended offline    Completed without error       00%     39931         -
# 9  Short offline       Completed without error       00%     39904         -
#10  Short offline       Completed without error       00%     39880         -
#11  Short offline       Completed without error       00%     39856         -
#12  Short offline       Completed without error       00%     39832         -
#13  Short offline       Completed without error       00%     39808         -
#14  Short offline       Completed without error       00%     39784         -
#15  Extended offline    Completed without error       00%     39763         -
#16  Short offline       Completed without error       00%     39736         -
#17  Short offline       Completed without error       00%     39712         -
#18  Short offline       Completed without error       00%     39688         -
#19  Short offline       Completed without error       00%     39664         -
#20  Short offline       Completed without error       00%     39640         -
#21  Short offline       Completed without error       00%     39616         -
```

---

### Post by SeijiSensei on 2014-02-25
What if you copy the file manually with cp or scp?  Same problem?

---

### Post by Ackis on 2014-02-25
> **SeijiSensei said:**
> What if you copy the file manually with cp or scp?  Same problem?

I hadn't thought of trying it from the command line (instead used my Windows box).

```

sudo cp "/backup/DNS-323-backup/John/Hard Drive - Reoverred Data/Pictures/08-August - Science Camp/08-August - Science Camp 019a.jpg" .
```

Worked with no error output and nothing added to /var/log/error /var/log/syslog

I also apparently can't spell Recovered.

---

### Post by Ackis on 2014-02-26
After moving the one file to my desktop that was causing rsync to stall, I ran it for all the directories I wanted to save:

```

sudo rsync -av --progress --delete --exclude "ffp" --exclude "lost+found" --exclude ".systemfile" --exclude "thumbs.db" --exclude "desktop.ini" /backup/DNS-323-backup/ /media/USB/backup/

```

These errors showed up, but rsync didn't hang at all.

```

John/Johns Documents/My Games/Skyrim/Saves/Save 51 - Ackis  Whiterun  29.46.34.ess
     8781806 100%    7.16MB/s    0:00:01 (xfer#1, to-check=1064/18198)
rsync: read errors mapping "/backup/DNS-323-backup/John/Johns Documents/My Games/Skyrim/Saves/Save 51 - Ackis  Whiterun  29.46.34.ess": Input/output error (5)
WARNING: John/Johns Documents/My Games/Skyrim/Saves/Save 51 - Ackis  Whiterun  29.46.34.ess failed verification -- update discarded (will try again).
John/Johns Documents/My Games/Skyrim/Saves/Save 51 - Ackis  Whiterun  29.46.34.ess
     8781806 100%    7.50MB/s    0:00:01 (xfer#2, to-check=1064/18198)
rsync: read errors mapping "/backup/DNS-323-backup/John/Johns Documents/My Games/Skyrim/Saves/Save 51 - Ackis  Whiterun  29.46.34.ess": Input/output error (5)
ERROR: John/Johns Documents/My Games/Skyrim/Saves/Save 51 - Ackis  Whiterun  29.46.34.ess failed verification -- update discarded.
Shared Docs/DVD Profiler/Collection/Images/097360724165.3b.jpg
      131051 100%   93.73MB/s    0:00:00 (xfer#3, to-check=2077/24143)
rsync: read errors mapping "/backup/DNS-323-backup/Shared Docs/DVD Profiler/Collection/Images/097360724165.3b.jpg": Input/output error (5)
WARNING: Shared Docs/DVD Profiler/Collection/Images/097360724165.3b.jpg failed verification -- update discarded (will try again).
Shared Docs/DVD Profiler/Collection/Images/097360724165.3b.jpg
      131051 100%   10.41MB/s    0:00:00 (xfer#4, to-check=2077/24143)
rsync: read errors mapping "/backup/DNS-323-backup/Shared Docs/DVD Profiler/Collection/Images/097360724165.3b.jpg": Input/output error (5)
ERROR: Shared Docs/DVD Profiler/Collection/Images/097360724165.3b.jpg failed verification -- update discarded.

```

I would have thought that rsync would give those type of errors for the original file that was causing issues as well.

---

### Post by SeijiSensei on 2014-02-26
Those input/output errors are often indicating physical errors on the device or, less likely though possible in your case, a poor network connection.  Have you tried connecting the NAS directly to the machine running rsync rather than using the network connection?

Rsync works best when all the devices have *nix filesystems like the ext4 filesystem that most Linux distributions use by default.  That's not the case here since you are using CIFS to mount the device.  (I wouldn't be surprised to learn that the device itself is formatted with FAT32 or NTFS as well.)  Does the NAS also have an NFS server?  Rsync would be happier with that since NFS mounts use the same primitives as ext4.

---

### Post by Ackis on 2014-02-26
The file system on the nas is ext2 and on the USB drive that I'm backing data up to is ext4.

I went with cifs due to samba and that my primary PC's are Windows machines.  Also I don't know a damn thing about how NFS works.

I asked about the NFS/Samba choice here in question 8:
[http://ubuntuforums.org/showthread.php?t=2202118](http://ubuntuforums.org/showthread.php?t=2202118)

Both my NAS devices support NFS.

---

### Post by Ackis on 2014-02-27
```

sudo rsync --archive --verbose --human-readable --progress --delete --itemize-changes --delete-excluded --exclude "ffp" --exclude "lost+found" --exclude ".systemfile" --exclude "thumbs.db" --exclude "desktop.ini" /backup/DNS-323-backup/$

```

This is my current rsync command and it's working after I've manually removed the three "offending" files.  I still have no idea why that first image caused it to stall opposed to erroring out. :(

If I decide to use NFS and Samba are there any added complexities that I should be aware of?

---

### Post by SeijiSensei on 2014-02-27
No, but you'll need to install the nfs-common package on the client machine as NFS support is not included by default.  On the NAS, it depends on what the manufacturer provides.  I'd use version 3 of NFS on the server if possible as it's a bit less touchy than NFSv4.

My Linux server offers up the same files via both NFS and Samba.  Most of the time I'm using a Linux client and mount my remote home directory with NFS.  When I use Windows, I connect to the same share with Samba.

Take a look at this HowTo, particularly the section on client-side configuration: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

By the way, I suggest using --include-from and --exclude-from and putting the entries into files. That works well if you find yourself adding or removing items over time, or if the list of exclusions is very long.  When I back up whole machines, my exclude-from file looks like this:
```

proc/
sys/
dev/
tmp/
/old/
Temp
/backup/
usr/share/doc
usr/man
usr/local/man
usr/share/man
usr/share/doc

```
along with any local customizations.

---

### Post by Ackis on 2014-02-27
Thanks for the suggestion for the --exclude-from, makes a lot more sense than listing them all individually.

Have you backed up Windows shares at all and if so do you have any recommendations on what to exclude?

My Linux server doesn't have any data so I don't have to worry about backing anything up on it (all the data resides on the NAS devices).  Maybe I might want to backup configuration files?

Back to the NFS, the Alt-F firmware with the DNS-323 has a NFS option.  I'm really going in blind with the options and there's a couple things I haven't been able to find.

This is the /etc/exports I have:
```

/mnt/md0 192.168.0.199(ro,sync,no_subtree_check)
/mnt/md0/Shared\040Docs/Media\040Server 192.168.0.199(rw,no_root_squash,no_subtree_check,anonuid=99,anongid=98)

```

I'm getting an error that "/mnt/md0/Shared\040Docs/Media\040Server" does not support mounting.  From what I've read that's because you can't have recursive mounts like that.

I ran out of time tonight but I still need to investigate the options and how the uid/gid's map and how to get them to map properly.

I'd like to have a ro and rw share, but according to [http://askubuntu.com/questions/313098/creating-two-nfs-shares-one-read-write-and-one-read-only](http://askubuntu.com/questions/313098/creating-two-nfs-shares-one-read-write-and-one-read-only) it's not exactly an easy thing to deal with.

Not sure if I'm asking anything specifically, I'm rambling as well, mainly taking notes for when I touch this again tomorrow.

I appreciate the help you've given.

---

