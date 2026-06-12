---
title: "Cannot access data on my EXT4 drive - help getting it back."
date: 2023-05-29
forum: General Help
---

### Post by elsmandino2 on 2023-05-29
Hi there.

I have done something a bit stupid and would be grateful to know if there is anything I can do to remedy it.

I have two Linux servers - both running Debian (Openmediavault) and I unmounted a USB hard drive from one with the intentions of mounting it in the other.

However, I pressed initialise instead by accident - the disk started to become wiped but I managed to shut it down after a few seconds.

Now I cannot access any data off the drive - it is 14TB in size with 12TB used.  However, only about 1TB is important to me.

Is there any way I might be able to get some of the data back?

---

### Post by oldfred on 2023-05-29
Was it all in one large partition?
Does testdisk find anything?

I have used photorec, it took all night on a 640GB  drive that was not full. It might take weeks on your drive.
And photorec does not recover full filename, just extension. I had saved many copies of some text files & sorting & comparing to old backup took weeks (part time) to resolve and still was not sure I got most updated version of all files.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) & 
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Your gpt drive has backup partition table at end of drive. Is it still valid?
sudo gdisk -l /dev/sdX where X is your drive.
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
More repair info  use p, v & w to write the partition table. If not correct just use q to quit. :

That will not bring back data, but you may be able to run e2fsck?
I would prefer to make image as backup, but you drive is so large, not sure you can do that?

---

### Post by elsmandino2 on 2023-05-29
Thanks very much for the advice - lots to try, there.

It was indeed a single partition.

As suggested, I am currently scanning the disk with testdisk - going to take over 24 hours, at the current rate.

Current messages as follows:

I am not quite sure whether that is encouraging or not.

I shall post back here, when it is finish (if that is OK) and I consider what my options then are.

---

### Post by oldfred on 2023-05-29
Please do not post in line. Just use the attachments.
Not everyone has high speed Internet.

I might have tried gdisk first to see if it would recover partition table.
If testdisk shows any files, immediately copy them. Some have seen files in testdisk, and closed it, and then never found files again.

---

### Post by dragonfly41 on 2023-05-29
I offer one suggestion for post recovery (although I have not tried this idea yet in testdisk data recovery).
If you end up with vast numbers of text files (corpora) where the filenames and structure are lost, you can apply techniques such as ripgrep to look for keywords *inside *each file.

There is also an App named AntConc which you can apply to vast corpora of text files to do concordance analysis. Natural language processing.
And there are cloud based versions such as SketchEngine.eu.  But I do suggest trying AntConc free first. The theme is concordance analysis and it will allow you to at least begin to categorise the text files and avoid weeks of detective work.

So it is like throwing a lorry of fruit into a grinder and looking for pips of knowledge in the juice.

---

### Post by elsmandino2 on 2023-05-30
Thank you for the further advice.

Can I just ask what the difference is between gdisk and fsck is, please?

I have also come across this:

[Data Recovery and File Undelete freeware for Linux files (r-studio.com)]("https://www.r-studio.com/free-linux-recovery/")

Which seems to do something quite similar as well.

---

### Post by yancek on 2023-05-30
gdisk is " **a text-mode menu-driven program for creation and manipulation of partition tables"**.

fsck is a filesystem check.

---

### Post by ActionParsnip on 2023-05-30
Are there no backup copies? If not....why not?

---

### Post by elsmandino2 on 2023-05-30
> **yancek said:**
> gdisk is " **a text-mode menu-driven program for creation and manipulation of partition tables"**.

fsck is a filesystem check.

Thanks for that.  So, depending upon what TestDisk finds, should I run gdisk or fsck first?

> **ActionParsnip said:**
> Are there no backup copies? If not....why not?

Annoyingly, I was trying to set up a backup disk when this all happened.

I do have some bits, hopefully, in the cloud but some stuff was not backed up.

---

### Post by oldfred on 2023-05-30
I think you need a partition table for fsck or e2fsck to work.
So either testdisk finds partition or gdisk. 

If not sure what a command is, use man:
man fsck
man e2fsck
man gdisk

---

### Post by elsmandino2 on 2023-05-30
I might be getting somewhere. I have received the two following screens with TestDisk.
[IMG]https://i.postimg.cc/tTsH78gQ/IMG-20230530-162521.jpg[/IMG][IMG]https://i.postimg.cc/prj20r3L/After.jpg[/IMG]
I have managed to get these two screens - any advice, on what to do now, would be much appreciated.

---

### Post by oldfred on 2023-05-30
Please see post #4.
Please do not post in line. Just use the attachments.
Not everyone has high speed Internet.

It says following partitions cannot be recovered. Not good.
And only one is large. Testdisk does find multiple versions, if you partitioned more than once or changed partitions.

Second screen show a lot of garbage or nothing that is a large partition. Did you have an ESP on that drive?
It looks like it is trying to convert random data into something like a partition, but cannot.

---

### Post by elsmandino2 on 2023-05-30
Sorry oldfred - not quite sure what posting in line is.  Would you mind clarifying what this, please, so I can avoid in future?

As far as I am aware, there should be an ESP.  I originally formatted it with Openmedivault and just used it as it was.

I think I might just have a go with gdisk, as you suggested - I am worried that TestDisk just isn't going to cut it, here.

---

### Post by wyattwhiteeagle on 2023-05-30
> **elsmandino2 said:**
> Sorry oldfred - not quite sure what posting in line is.  Would you mind clarifying what this, please, so I can avoid in future?

As far as I am aware, there should be an ESP.  I originally formatted it with Openmedivault and just used it as it was.

I think I might just have a go with gdisk, as you suggested - I am worried that TestDisk just isn't going to cut it, here.

In-line posting refers to attaching images such as what you are posting.

Best to type the info then enclosing it inside code tags...quote tags...etc

In "Advanced Reply" and "Reply with Quote" across the top of where you type...the hashtag symbol is the "code" tags
highlite what needs to be in "code" tags then click the hashtag at the top.

---

### Post by elsmandino2 on 2023-05-30
Sorry - shall make sure I used code from now on.

Here is what I have so far:

```
Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Tue May 30 19:25:18 2023 from 192.168.1.100
root@omvtemp:~# lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   5.5T  0 disk
&#9492;&#9472;sda1   8:1    0   5.5T  0 part /srv/dev-disk-by-uuid-63c34541-0fd4-4ffc-bc49-2
sdb      8:16   0   1.8T  0 disk
&#9492;&#9472;sdb1   8:17   0   1.8T  0 part /srv/dev-disk-by-uuid-39cd1bac-1f3e-473c-8743-a
sdc      8:32   0 465.8G  0 disk
&#9492;&#9472;sdc1   8:33   0 465.8G  0 part /srv/dev-disk-by-uuid-dc07c53d-d6a0-4027-a500-5
sdd      8:48   0  59.6G  0 disk
&#9500;&#9472;sdd1   8:49   0  58.7G  0 part /
&#9500;&#9472;sdd2   8:50   0     1K  0 part
&#9492;&#9472;sdd5   8:53   0   975M  0 part [SWAP]
sde      8:64   0   4.5T  0 disk
&#9492;&#9472;sde1   8:65   0   4.5T  0 part /srv/dev-disk-by-uuid-bcaf61dd-18c0-45c6-ac6d-e
sdf      8:80   0  12.7T  0 disk
&#9492;&#9472;sdf1   8:81   0  12.7T  0 part
root@omvtemp:~# gdisk /dev/sdf
GPT fdisk (gdisk) version 1.0.6


Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present


Found valid GPT with protective MBR; using GPT.


Command (? for help):
```

Does this assist in any way?

---

### Post by oldfred on 2023-05-30
Try this its an el, not cap I nor 1 (one), font is not always clear
sudo gdisk -l /dev/sdf 

Sometimes you have to use screenshots, but you can easily attach them in forum's advanced editor and paperclip icon.
If photo, no need for high resolution as most screens will not show it anyway, so reduce size first.
In forum's advanced editor also is an easy way to add code tags, highlight code and click # icon.

---

### Post by elsmandino2 on 2023-05-30
Thanks for all the pointers - still getting used to some of these forum customs :)

```
root@omvtemp:~# sudo gdisk -l /dev/sdf
GPT fdisk (gdisk) version 1.0.6


Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present


Found valid GPT with protective MBR; using GPT.
Disk /dev/sdf: 27344699392 sectors, 12.7 TiB
Model: Elements 25A3
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): AA68BD0E-4889-453F-A041-8394B5248F55
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 27344699358
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048     27344699358   12.7 TiB    8300

```

---

### Post by oldfred on 2023-05-30
That is still showing valid partition table.

I might try e2fsck.
We know it is sdf, but always check before running any command that uses device like /dev/sdf to be sure it has not changed.
My flash drives become hd0 or sda and then every other drive changes.

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdf1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sdf1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdf1

You may need this:
List backup superblocks:
sudo dumpe2fs /dev/sdf1 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sdf1

---

### Post by elsmandino2 on 2023-05-30
Thanks for sticking with me on this - really appreciate it.

Ran the two commands and got the following:

```
root@omvtemp:~# sudo e2fsck -C0 -p -f -v /dev/sdf1
e2fsck: Bad magic number in super-block while trying to open /dev/sdf1
/dev/sdf1:
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>


root@omvtemp:~# sudo e2fsck -f -y -v /dev/sdf1
e2fsck 1.46.6 (1-Feb-2023)
ext2fs_open2: Bad magic number in super-block
e2fsck: Superblock invalid, trying backup blocks...
Superblock has an invalid journal (inode 8).
Clear? yes


*** journal has been deleted ***


The filesystem size (according to the superblock) is 3418095355 blocks
The physical size of the device is 3418087163 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort? yes




Server: ***** FILE SYSTEM WAS MODIFIED *****
root@omvtemp:~#
```

---

### Post by oldfred on 2023-05-30
I would not have deleted journel, sometimes that helps recovery.

You can list backup superblocks, depending on what was deleted, you may have to try a lot, early one's may also be damaged.

---

### Post by elsmandino2 on 2023-05-30
Sorry am just blindly copying and pasting commands out of desperation.

```
root@omvtemp:/# sudo dumpe2fs /dev/sdf1 | grep -i backup
dumpe2fs 1.46.6 (1-Feb-2023)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sdf1

```

---

### Post by oldfred on 2023-05-30
It cannot seem to find superblocks.
I thought that since now you seem to have a valid partition, it might find the backup superblocks. But if too many were deleted command fails.

This command tries to recover data using journel, but you posted that you deleted it.
man ext4magic
sudo ext4magic /dev/sdd2 -a $(date -d "-120hours" +%s)

I saved these older links, not sure if they may help or not.
Last ditch redo superblocks, see post #49:
[http://ubuntuforums.org/showthread.php?t=1681972&page=5](http://ubuntuforums.org/showthread.php?t=1681972&page=5)
Worked for this user:
[http://ubuntuforums.org/showthread.php?t=2033778](http://ubuntuforums.org/showthread.php?t=2033778)
[http://ubuntuforums.org/showthread.php?t=1684746](http://ubuntuforums.org/showthread.php?t=1684746)
Some additional advanced ways:
[http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/](http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/)
[http://www.hanksaves.com/hddrecovery/index.php/Welcome_to_Hank%27s_Data_Recovery_Wiki](http://www.hanksaves.com/hddrecovery/index.php/Welcome_to_Hank%27s_Data_Recovery_Wiki)

---

