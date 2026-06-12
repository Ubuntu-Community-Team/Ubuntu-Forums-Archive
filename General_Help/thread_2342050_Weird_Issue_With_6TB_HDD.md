---
title: "Weird Issue With 6TB HDD"
date: 2016-11-03
forum: General Help
---

### Post by ThePowerpuffGirls on 2016-11-03
IN JAnuary I bought a WD 6TB HDD from BEstBUy.
LAtely, it's been slow, such as when I open a picture, and go to the next, it would hang/freeze. THe other week, I was trying to copy a folder to it, and it was hang at %11 percent. I deleted some files out of it, and it would freeze at 17%, so maybe there were some corrupted files, so I deleted the folder, and after restart, the remaining folder didn't appears to be on the HDD. Maybe that was where it began.

I did some sorting and sorted my files on it, organised them.
Another thing is, Ubuntu would hang during shutdown. I would press F11, Many times I start back up, it would hang after the logging in before getting to the desktop, and during those times, the external HDD wouldn't show up on the sidebar. I would have to restart again for it to do so.

I am trying to wipe the remaining drive space 1.3 TB, and it would hang, the screen keeps dimming like it's a crash, and the progress bar won;t move, instead the ETA keeps getting higher and higher. It would sometimes make a weird sound, the same as if you press down on a 2.5 HDD while it's running.

In the SMart disk manager (I think that's what it's called), it says the disk is OK (6 bad sectors).
I've been able to copy stuff to and from it, generally. I organised it the other day, moved files around to different folders, plus deleted some.

Would anyone know what is wrong and how to fix it? I have it still wiping in case the will eventually finish. I'm using the latest version of BleachBit.
I have UBuntu 16.04 x64 installed.
SAMSUNG 250GB SSD M.2
ASUS Z97-K motherboard.
Intel i5-4670K processor.
The HDD is connected via SATA, BIOS set to AHCI, bott devices and everything set to UEFI, or UEFI first.

Update: I just checked and Bleachbit gave an input-output error. I restarted and trying again. THe folders appeared to be empty but now everything appears back.

---

### Post by kpatz on 2016-11-03
Sounds like the disk is defective.  Any bad sector in a modern drive is a cause for concern.

Run this command and post the output (substitute your 6 TB drive's device for /dev/sdb):
```
sudo smartctl -a /dev/sdb
```

---

### Post by oldfred on 2016-11-03
Post this:
  sudo parted /dev/sda unit s print 

If you forced a process to stop, then you may have created some corruption and should run fsck.
      
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by ThePowerpuffGirls on 2016-11-03
I have it wiping right now. The progress bar went a lot fursther now, almost a curarter I think. I will leave it until I get back, in a few hours. I will post the output.

Thank you. :)

---

### Post by ThePowerpuffGirls on 2016-11-03
> **kpatz said:**
> Sounds like the disk is defective. Any bad sector in a modern drive is a cause for concern.

Run this command and post the output (substitute your 6 TB drive's device for /dev/sdb):
```
sudo smartctl -a /dev/sdb
```

sudo: smartctl: command not found

> **oldfred said:**
> Post this:
  sudo parted /dev/sda unit s print 

If you forced a process to stop, then you may have created some corruption and should run fsck.
      
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Model: ATA WDC WD60EZRZ-00R (scsi)
Disk /dev/sda: 11720979633s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start  End           Size          File system  Name  Flags
 1      2048s  11720978431s  11720976384s  ntfs               msftdata


For the bottom command:
I get: "/dev/sda1: 
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>"

It is an NTFS partition.

Update. Since Bleachbit was unable to finish, it left two large files with very large file names on my external HDD. I'm unable to delete them, whether through bleachbit or root.

---

### Post by kpatz on 2016-11-03
Run ```
sudo apt-get install smartmontools
``` and then retry the smartctl command: ```
sudo smartctl -a /dev/sda
```

e2fsck doesn't work on NTFS partitions, use ntfsfix instead:```
sudo ntfsfix /dev/sda1
```

---

### Post by oldfred on 2016-11-03
You could have mentioned it was NTFS as fsck cannot be done on NTFS.
Linux' ntfsfix does very little. It cannot do the full fixes possibly required.
You have to run chkdsk from Windows.
Did you mount drive with a newer Windows when last used? That would leave it in hibernated state where only Windows can get to it.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[URL="http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions"]http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions
[/URL]
 More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation) 



[URL="http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions"]
[/URL]

---

### Post by ThePowerpuffGirls on 2016-11-04
I didn't know it was NTFS, until I looked. The good news is that I have backed up data, only lost a few shows because I was tired and rushed through it. It took a long time to move stuff over...

It was never accessed through Windows, only Ubuntu.

I was able to format it to EXT4, and now wiping the drive. It'll be done in less than an hour and will follow through with your replies.
It still has 3 bad sectors, I'm wondering if it is recommended to move stuff back on a drive with bad sectors or is that normal?
I will also do the same for the 4TB as that is also NTFS.

I had them NTFS in case I wanted to access them through Windows, but never do.

Weird thing is, when I wipe-deleted (correct phrase), deleted files via Bleachbit, I left folders and files with long file names with random letters, numbers and characters. When I tried to remove them, it said that there was no such file or directory.

When I ran ntfsfix, it said the volume was corrupted and didn't have permissions, but still was able to access and move files over to another HDD. It was really weird.
I don't trust the NTFS as I commonly get errors and stuff on drives with the FS and it's Microsoft.

---

### Post by kpatz on 2016-11-04
If you only use it in Ubuntu and not Windows then it's best to format it as ext4.  I'd still install smartmontools and get the SMART info with these two commands:

```
sudo apt-get install smartmontools
sudo smartctl /dev/sda
```

---

### Post by ThePowerpuffGirls on 2016-11-04
> **oldfred said:**
> Post this:
sudo parted /dev/sda unit s print 

If you forced a process to stop, then you may have created some corruption and should run fsck.

#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

I ran the script:
> alexa@Alexas-PC:~$ sudo e2fsck -C0 -p -f -v /dev/sdb1
6TB:                                                                            /lost+found not found.  CREATED.
                                                                               
          11 inodes used (0.00%, out of 183140352)
           0 non-contiguous files (0.0%)
           0 non-contiguous directories (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 2
    11591017 blocks used (0.79%, out of 1465122048)
           0 bad blocks
           1 large file


           0 regular files
           1 directory
           0 character device files
           0 block device files
           0 fifos
           0 links
           0 symbolic links (0 fast symbolic links)
           0 sockets
------------
           1 file



Also, BleachBit said it was 0% full but still 35 minutes remaining. I never got that before, but I also never formatted a 6TB drive before.

---

### Post by ThePowerpuffGirls on 2016-11-04
> **oldfred said:**
> Post this:
sudo parted /dev/sda unit s print 

If you forced a process to stop, then you may have created some corruption and should run fsck.

#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

I ran the script:
```
alexa@Alexas-PC:~$ sudo e2fsck -C0 -p -f -v /dev/sdb1
6TB:                                                                            /lost+found not found.  CREATED.
                                                                               
          11 inodes used (0.00%, out of 183140352)
           0 non-contiguous files (0.0%)
           0 non-contiguous directories (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 2
    11591017 blocks used (0.79%, out of 1465122048)
           0 bad blocks
           1 large file


           0 regular files
           1 directory
           0 character device files
           0 block device files
           0 fifos
           0 links
           0 symbolic links (0 fast symbolic links)
           0 sockets
------------
           1 file

```

> **kpatz said:**
> If you only use it in Ubuntu and not Windows then it's best to format it as ext4. I'd still install smartmontools and get the SMART info with these two commands:

sudo apt-get install smartmontools
```
sudo smartctl /dev/sda
```

```

alexa@Alexas-PC:~$ sudo smartctl /dev/sdb1
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-45-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")


ATA device successfully opened


Use 'smartctl -a' (or '-x') to print SMART (and more) information

```

I try to to install:
```
alexa@Alexas-PC:~$ sudo apt-get install smartctl -a
E: Command line option 'a' [from -a] is not understood in combination with the other options.
alexa@Alexas-PC:~$ sudo apt-get install smartctl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package smartctl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'smartctl' has no installation candidate

```

Also, BleachBit said it was 0% full but still 35 minutes remaining. I never got that before, but I also never formatted a 6TB drive before.

Update: I notice that it doesn't say 3 bad sectors anymore.
I'm doing a SMART Self Test right now.
I'm not sure what would have made the bad sectors and made them disappear. Could it have been an error?

Update:
The short self-test has been running for over 20 minutes now, is that normal? It never took that long for me before. It seems to be stuck at "10% remaining".

---

### Post by oldfred on 2016-11-04
Never seen a 6TB drive either, would expect everything to take longer.

Most drives get a few bad sectors & they get allocated out. Only if number of bad sectors grows a lot particularly in a short time would I worry.

Do you really need/want one extremely large 6TB partition? If storing movies maybe you do.
But for most uses it may be better to have more than one partition. Then repairs can run in less time.

---

### Post by gordintoronto on 2016-11-05
It seems likely that the drive has failed or is about to fail. (It's also possible that it's a cable problem.)

I think Ubuntu includes a program called Disks. Run it, highlight the drive, tell us what it says under "Assessment".

---

