---
title: "PulseAudio problem"
date: 2013-09-06
forum: General Help
---

### Post by impinball on 2013-09-06
I am not completely new to Linux, but I'm not the most familiar with it, either. I'm not going to put a large amount of detail into this, but enough to give an idea of what it is.

[LIST=1]
[*]I am having issues with specifically PulseAudio sound output. ALSA works fine, and still outputs its sound like it should (speaker-test works), but PulseAudio gives nothing. Even after a clean re-install of both, ALSA works just as well, but PulseAudio works equally not as well
[*]The issues are based on permissions of my home directory being out of whack. The owner of my /home directory is root, and so is my user directory (which is especially an issue). My biggest dilemma with this is that chown doesn't work--it runs as if it does every single operation successfully, but when I run ls -la /home, the owner still shows up as root, indicating that chown is not changing a thing.
[*]The drive affected is an NTFS partition, also used for similar purposes by Windows. The /home directory is mounted to this partition, and I'm working on getting it mounted as C:\Users in Windows 7 as well (which I already know how, but I'm asking around in those circles to see the safer of the two options I have).
[/LIST]
This clearly isn't of a single category, and is a little complex in nature.
My biggest question is this: where is the most appropriate forum for this issue?

---

### Post by newb85 on 2013-09-06
I'm curious, what is the output of
```
head -n 1 /etc/passwd
```

---

### Post by Crusty Old Fart on 2013-09-06
Well, since you are not an "Absolute" beginner. Your thread probably doesn't belong in this forum. Since there are several issues involved with the difficulty you're having, a better place to have started the thread would have probably been in --> [General Help](http://ubuntuforums.org/forumdisplay.php?f=331)

It seems to me that the problem with chown not working for you is that you're trying to do it on directories that reside on an NTFS partition. Although Linux can mount and access NTFS partitions, they aren't really as compatible with Linux as the ext2, ext3, and ext4 file systems are. I've never known of anyone trying to chown or chmod anything on an NTFS partition, so I could be completely wrong about the filesystem format of NTFS being the problem, But, that's my best guess. If I were you, I'd move my /home directory to an ext type partition.

Good Luck.

---

### Post by QIII on 2013-09-06
Yes, better here and with a better title

---

### Post by Bashing-om on 2013-09-06
WUBI ????impinball;
 
EDIT: WUBI ????

Let's get some background stuff out of the way.
Though there is an effort in NTFS3g development to incorporate linux file permissions onto NTFS ... not implemented in general use at this time.
These file permissions are set when the NTFS partition is mounted:
See:
[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite)

Now .. filesystems; Windows runs and uses the NTFS file system - that ubuntu can read and write to - ,but,  ubuntu uses/runs on the EXT(4) family of file systems. You want ubuntu installed on the proper format !
Show us the disk(s) partitioning; terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f
sudo blkid

```
and further advise is pending.

For the permissions issue: Will await the return on newb85's request. 

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by impinball on 2013-09-06
> **QIII said:**
> Yes, better here and with a better title
If you wouldn't mind, go ahead and move the following post to here: [http://ubuntuforums.org/showthread.php?t=2172645](http://ubuntuforums.org/showthread.php?t=2172645).
I'm going to update the main area of content accordingly.

---

### Post by newb85 on 2013-09-06
Let me suggest an alternative to putting your /home directory on an NTFS partition and merge it with your C:/Users directory, which seems to be the root of the problem.

What if instead, you put /home on an Ext4 partition, and replace the Documents, Music, Downloads, etc. directories in your /home directory with links to their corresponding directories in your C:/Users directory?  I'm assuming that would achieve the scenario you're pursuing...

---

### Post by impinball on 2013-09-06
Also, here's the output of each command you two asked for:

newb85:
```
root:x:0:0:root:/root:/bin/bash
```

Bashing-on (I only have the /home mounted on NTFS--the rest are properly installed on ext4 partitions):
```
$ sudo fdisk -lu
/dev/sda1            2048      206847      102400   de  Dell Utility/dev/sda2   *      206848    20686847    10240000    7  HPFS/NTFS/exFAT
/dev/sda3        20686848   261859499   120586326    7  HPFS/NTFS/exFAT
/dev/sda4       261875561   625141759   181633099+   f  W95 Ext'd (LBA)
/dev/sda5       261875624   310922009    24523193    7  HPFS/NTFS/exFAT
/dev/sda6       310922074   445129019    67103473    7  HPFS/NTFS/exFAT
/dev/sda7       445143040   617033727    85945344   83  Linux
/dev/sda8       617035776   625141759     4052992   82  Linux swap / Solaris

$ sudo parted -l
/dev/sda1            2048      206847      102400   de  Dell Utility
/dev/sda2   *      206848    20686847    10240000    7  HPFS/NTFS/exFAT
/dev/sda3        20686848   261859499   120586326    7  HPFS/NTFS/exFAT
/dev/sda4       261875561   625141759   181633099+   f  W95 Ext'd (LBA)
/dev/sda5       261875624   310922009    24523193    7  HPFS/NTFS/exFAT
/dev/sda6       310922074   445129019    67103473    7  HPFS/NTFS/exFAT
/dev/sda7       445143040   617033727    85945344   83  Linux
/dev/sda8       617035776   625141759     4052992   82  Linux swap / Solaris

$ sudo parted /dev/sda unit s print
Model: ATA ST9320423AS (scsi)
Disk /dev/sda: 625142448s
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start       End         Size        Type      File system     Flags
 1      2048s       206847s     204800s     primary   fat16           diag
 2      206848s     20686847s   20480000s   primary   ntfs            boot
 3      20686848s   261859499s  241172652s  primary   ntfs
 4      261875561s  625141759s  363266199s  extended                  lba
 5      261875624s  310922009s  49046386s   logical   ntfs
 6      310922074s  445129019s  134206946s  logical   ntfs
 7      445143040s  617033727s  171890688s  logical   ext4
 8      617035776s  625141759s  8105984s    logical   linux-swap(v1)

$ sudo lsblk -f
NAME   FSTYPE LABEL MOUNTPOINT
sda                 
&#9500;&#9472;sda1              
&#9500;&#9472;sda2              
&#9500;&#9472;sda3              
&#9500;&#9472;sda4              
&#9500;&#9472;sda5              
&#9500;&#9472;sda6              /home
&#9500;&#9472;sda7              /
&#9492;&#9472;sda8              [SWAP]
sr0                 

$ sudo blkidt
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="3400418A00415450" TYPE="ntfs" 
/dev/sda3: LABEL="OS" UUID="245612265611F8EE" TYPE="ntfs" 
/dev/sda5: UUID="BE8C34218C33D29F" TYPE="ntfs" 
/dev/sda6: LABEL="My Files" UUID="01CE89F2EF8C8DE0" TYPE="ntfs" 
/dev/sda7: UUID="adf43616-b5bb-4d95-b2ea-1fd97326af98" TYPE="ext4" 
/dev/sda8: UUID="9078ce75-a9eb-4e38-a7f2-7fd09e600b67" TYPE="swap" 
```

I don't know if anything needs edited out, but if so, go ahead and take care of whatever needs edited.

Also, if you want more detail on things I've already tried, this is the original forum thread: [http://ubuntuforums.org/showthread.php?t=2172645](http://ubuntuforums.org/showthread.php?t=2172645). I do have one request: please reply about anything on either thread on this thread only.

---

### Post by impinball on 2013-09-06
I made a mistake. Here are the actual links to the posts and a little background of the two.
1. [http://ubuntuforums.org/showthread.php?t=2165204](http://ubuntuforums.org/showthread.php?t=2165204) - This is the initial thread that I created to try to get the problem fixed.
2. [http://ubuntuforums.org/showthread.php?t=2172645](http://ubuntuforums.org/showthread.php?t=2172645) - This is the thread that I created to summarize my initial thread.

---

### Post by Bashing-om on 2013-09-06
impinball; Well.. 

observations; Partitioning -> do not see how it would affect the current situations but ;;
/dev/sda4 -> 625141759
/dev/sda8 -> 625141759 
Not good, need to move ubuntu's swap partition out of Windows' extended partition space.

And I go along with the others .. ubuntu /home on a Windows file system NTFS not a good arrangement. To share files use a common NTFS data partition.

[INDENT][INDENT]just my thoughts
[/INDENT][/INDENT]

---

### Post by impinball on 2013-09-06
> **Bashing-om said:**
> impinball; Well.. 

observations; Partitioning -> do not see how it would affect the current situations but ;;
/dev/sda4 -> 625141759
/dev/sda8 -> 625141759 
Not good, need to move ubuntu's swap partition out of Windows' extended partition space.

And I go along with the others .. ubuntu /home on a Windows file system NTFS not a good arrangement. To share files use a common NTFS data partition.
[INDENT][INDENT]just my thoughts
[/INDENT]
[/INDENT]

I don't exactly know how to fix the former, but the problems with the latter didn't show up until well after I made the mount (which itself wasn't immediately after installation, but was soon thereafter).

---

### Post by Bashing-om on 2013-09-06
impinball;

Well,,, If it were me .. I would 
a) copy off my /home to an external source
then
b) fire up GParted from a liveDVD;
Try and move the swap partition a bit ( will have to unmount that swap partition-> R click on the key icon)
and
reformat /home as ext4 
copy the data (/home) back onto the newly formated partition.

It is likely that the UUID will change, in any event /etc/fstab will require editing to reflect the changes.
 
From the liveDVD ->mount the / partition:
```

sudo blkid ##to get the new UUID
sudo mkdir /mnt/work
sudo mount /dev/sda7 /mnt/work ##root is sda7 where /etc/ resides
sudo cp /etc/fstab /etc/fstab06sep13 ##just to keep safe
gksudo gedit /etc/fstab
##to make it similar, change the UUID to match above sda6##
##UUID=29a6fc4f-ff12-4cac-8eb1-e98e50f1107f /home           ext4    defaults        0       2 ##

```
save the file - exit back to terminal

and MUST release what has been manually mounted !
```

sudo umount /mnt/work

```
Reboot into the install and see what is.

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by impinball on 2013-09-07
I do have a few specific curiosities about doing that, first: would it be possible to mount only one specific folder from another partition into the Ubuntu filesystem (e.g. mount <username>/documents in that partition to /home/documents)? I would be willing to do that one at a time repeatedly if it is. That would make things a little easier to maintain (which is why I created that separate partition in the first place), and at the same time it would relieve my need to mount it as C:\Users in Windows (the Windows equivalent of /home).

The other thing is: how would I fix that Windows extended partition issue? The crazier thing about that is that the extended partition only appears to span the first partition within Windows, and not even the one that immediately follows. If I could remove the extended partition, but keep the partitions inside it, how would I do that. Or at the very least, how would I be able to move that extended partition out of the Ubuntu installation (the ext4 and swap partitions are right next to each other, and are the last two partitions on the hard drive)

---

### Post by impinball on 2013-09-07
Also, I do NOT want to format the partition /home is currently mounted to (it is where I keep all my personal data, such as documents and music, and is used across OSes).

---

### Post by newb85 on 2013-09-07
> **impinball said:**
> first: would it be possible to mount only one specific folder from another partition into the Ubuntu filesystem (e.g. mount <username>/documents in that partition to /home/documents)? I would be willing to do that one at a time repeatedly if it is. That would make things a little easier to maintain (which is why I created that separate partition in the first place), and at the same time it would relieve my need to mount it as C:\Users in Windows (the Windows equivalent of /home).

That's basically what I recommended in my last post yesterday.  Only I suggested that you link to the folders in your NTFS partition, because you "mount" an entire partition or drive, not just folders within that partition or drive.

> **impinball said:**
> If I could remove the extended partition, but keep the partitions inside it, how would I do that. 

I don't think that's possible.

> **impinball said:**
> Or at the very least, how would I be able to move that extended partition out of the Ubuntu installation (the ext4 and swap partitions are right next to each other, and are the last two partitions on the hard drive)
I assume you mean place the extended partition after the Ubuntu partitions.  This would not be trivial, and if I'm not mistaken, Windows will not be satisfied to be after Ubuntu on the drive.

---

### Post by impinball on 2013-09-07
> **newb85 said:**
> I assume you mean place the extended partition after the Ubuntu partitions.  This would not be trivial, and if I'm not mistaken, Windows will not be satisfied to be after Ubuntu on the drive.
Not exactly--I mean to simply resize the extended partition to not contain the two partitions that Ubuntu is contained in. On the other hand, it isn't that big of a problem, considering the two Ubuntu partitions haven't been adjusted since I first installed the OS.

On the other hand, simply mounting the partition to its own subdirectory of the root folder (path being something along the lines of [FONT=courier new]"/.my_files_partition"[/FONT]) and making a [FONT=courier new]"hard link/symlink"[/FONT] from my [FONT=courier new]"/home/<user>"[/FONT] folders to ones on that partition would work. I don't know how to do that, but I know it *is* possible, considering that a lot of programs, mostly system ones, make use of a lot of those. I would like to know which of the two would be better, and how I would accomplish it.

Here's what I was thinking as a possible way to fix this and get my /home directory still on an ext4 partition while still having the ability of keeping the NTFS in-between partition in easy access for the whole reason I made it in the first place: I could copy most things from that folder to a temporary one (strategically avoiding specific folders for a reason) and unmount the partition from that directory. Afterwards, I would copy most of the folders (all but two of the hidden folders--those are for Windows applications, and I would just copy the documents/etc. folders themselves) into /home. I would, then, mount the partition to a first-level directory as I previously mentioned (a.k.a. [FONT=courier new]"/.my_files_partition"[/FONT], [FONT=courier new]"/.my_files"[/FONT], [FONT=courier new]"/.my_data"[/FONT], etc.). I would create a hard link or symlink from specific Ubuntu directories to specific folders in that directory ([FONT=courier new]"~/Documents"[/FONT] to [FONT=courier new]"/.my_files/Documents"[/FONT], etc.). I would try to fix the permissions issue by chown-ing everything after this step, and I shouldn't run into nearly the problems I had previously. I would likely leave out some strategic directories (e.g. [FONT=courier new]"~/.pulseaudio"[/FONT], etc.) to let them rebuild themselves, likely lessening the potential of the problem resurfacing.

I may need a little help with how to do the mounts and what to tack on to the [FONT=courier new]cp[/FONT] command, but I can figure that out by myself. What I *will *need help to do is how to make the links between the two directories after both mounts.

---

### Post by newb85 on 2013-09-07
When copying, I would recommend that you use the -p option to preserve the permissions and timestamps.

I think you can find all you need to know about creating the symlinks with
```
man ln
```

---

### Post by impinball on 2013-09-14
By the way, I'm running into issues with me unmounting /home: I can't figure out how to get around the running processes causing the issues (I could tell that it was because there were processes using it). I couldn't figure out how to use lsof to get a list of all processes using the mounted partition to unmount it. I have been storing all my Linux-specific /home files (a.k.a. not Documents, etc.) on a directory I created called /tmphome (which is effectively a backup of these things).

I've already picked up that I'll need a live USB for the, but (excluding minor details) would this be as simple as changing the /etc/fstab for the computer's filesystem to not mount there and copying everything in /tmphome back over to /home? I could edit it to mount instead to /my_files, copy everything from /tmphome over afterwards, using a temporary profile and a terminal running sudo -i to delete whatever directories were automatically created and then replace the files I had stored in the /tmphome directory.

---

### Post by Bashing-om on 2013-09-14
impinball; Hey ;
In order to access/manipulate files that might otherwise be in use;
From the liveDVD - Terminal codes:
```

sudo mkdir /mnt/working ##to make a mount point
sudo mount /dev/sda1 ##assuming that your home is within the "/" directory AND that "/" is sda1.
##otherwise to see what is:
sudo fdisk -lu

```
Follow the same procedure to mount the file system containing "/tmphome" if it is elsewhere than "/"; making a different mountpoint.

With both mounted, should be able to do whatever you want.. 
Advisory: as you are aware, messing about with your /home directory can render it unaccessable, take care and exercise caution in what you change ! Take notes to be able to revert in the event of a mishap.

Important: one must (UN-)mount those manually mounted devices - else file system corruption - at some level - will result !
```

sudo umount /mnt/working

```

[INDENT][INDENT][INDENT]hope this helps
[/INDENT][/INDENT][/INDENT]

---

### Post by impinball on 2013-09-15
I will have a few issues with that for the following reason (and thus will not do them):
1. The /tmphome dir is not its own partition--I currently have all but my actual /home directory on the same ext4 partition.

---

### Post by Bashing-om on 2013-09-15
impinball; Good morning ,
It is indeed a good practice never to blindly do anything one does not understand, kudos !

To bolster your confidence:
Go ahead and mount your present partition containing your /home directory as per direction; from the liveDVD.
In terminal take a look at what is accessible:
```

ls -la /mnt/working/home/<your_user_name>

```
Change the path to see any other directories/files contained in that mounted partition.
If your "/tmphome" is in the same partition as your "/home" directory, then there exist no problem to directly copy any files you desire straight across.
I might suggest in order to preserve permissions on the copy that the "p" option be used.

Remember, you must (UN-)mount the mounted partition(s) when finished.

[INDENT][INDENT]hey, just try'n to help
[/INDENT][/INDENT]

---

