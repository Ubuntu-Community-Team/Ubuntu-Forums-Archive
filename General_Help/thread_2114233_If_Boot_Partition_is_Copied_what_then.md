---
title: "If Boot Partition is Copied what then?"
date: 2013-02-09
forum: General Help
---

### Post by Mark_in_Hollywood on 2013-02-09
I have deleted the former partitions on which Woindows sat. Now that they have been deleted, GParted calls that partition /sda1. (It used to be /sda1 and /sda2.) I want to copy the /sda3 (boot partition) to the /sda1.

What steps will I then take for GRUB2 to understand that something has changed?

1 - Do I mark the copied partition as boot in GParted?

2 - As long as GRUB2 sees /sda1 as the boot partition, does it matter if I don't delete the current /sda3 just yet? This is my fail-safe. If it blows up, I want a bootable 'puter. 

2 - What changes do I make in /etc/fstab before closing this LiveUSB session and rebooting?

---

### Post by oldfred on 2013-02-09
Normally not a good idea to renumber partitions. But Ubuntu primarily uses UUIDs so device numbers like /dev/sda3 are less important. But if you attempt to copy a partition with gparted it will also copy UUID and you cannot have duplicate UUIDs. Then you have to manually change UUID and update fstab & reinstall grub. 

Whatever you decide to do make sure you have good backups.

Partitions do not have to be in order. You could just make the sda1 a data partition in ext4 format. Or you can delete it and move the start of sda3 left into the unallocated and expand to include all the space. I normally do not like moving partitions left. It is both slower as all data is rewritten and any interruption by user or power failure will totally corrupt system. But it will work. 

All of the changes need to be with liveCD or flash and swap unmounted. You cannot work on mounted partitions (little key icon in your screenshot shows the mounted partitions).

---

### Post by Mark_in_Hollywood on 2013-02-09
If GParted copies /sda3 to /sda1 it harms itself as it copies the UUID? OR if /sda3 is copied to /sda1 I then must delete /sda3?

I have to manually change the UUID of /sda3 BEFORE copying?

Sorry for screenshot. I was just getting started this morning. Attached LiveUSB of GParted.

As for stable electricity, etc. I live in a big city and few electrical problems currently. I also have uninterruptable power supply, although that would supply 30 minutes, max. Just sayin'.

Lastly, if I make the /sda1 a "data partition" do you know if MythTV is "smart" and can be told to use it and another partition, if one partition gets nearly full? This would be the best solution for me. OR can the grub2/fstab be told to use both /sda5 (/home) and /sda1 for "data"?

In my ignorance of how Linux operates, I somewhat assumed that the way to do this is to copy the root to /sda1, delete /sda3, expand /sda1 to include former space of /sda3 and then to expand /sda5 to use 55 of the 60 gig available in /sda1. (As I type this I see I cannot put in words whether I understand what I am trying to explain.)

For reference:

ubuntu@ubuntu:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 Feb  9 00:56 0ac46a28-6e61-4dc4-b144-a792803ff60b -> ../../sda6
lrwxrwxrwx 1 root root 10 Feb  9 00:57 36cdd55c-9079-4455-8627-c3b8bfda3a45 -> ../../sda5
lrwxrwxrwx 1 root root 10 Feb  9 00:57 a19439e8-8efd-460b-8014-4a442c19628c -> ../../sda3
lrwxrwxrwx 1 root root 10 Feb  9 00:57 fd7584d6-3286-4365-8101-0451d1c5bc2e -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb  9 00:57 1885-CB82 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Feb  9 00:56 5c9a6ed1-2994-4549-b87c-735f94f1cb55 -> ../../sdc1

---

### Post by oldfred on 2013-02-09
I do not have myth, but those that I have seen usually have a small / (root) partition and a monster partition or drive just for the files. A few have used a small SSD from the system and a large drive for files. I do not think myth data is normally in /home, but do not know for sure.

You can mount partitions separately with fstab and link it into /home or mount directly into /home. I now keep /home inside root and have all data in data partitions on another drive. 

I prefer just reinstalling, especially if you have separate /home or data partitions. It is quick, easy if you have planned ahead a bit. 

If you use gparted to copy /, you will have to change UUID of one or the other partitions, probably edit fstab and reinstall grub.

---

### Post by Mark_in_Hollywood on 2013-02-09
Thank you for your help again, OldFred.

For now, it' too much information and I'm overwhelmed. It's news to me that I can have a second drive with data on it and another drive for the 12.04 OS. (or any other higher numbered OS).

What do you think about moving all the data to the right?

I could expand the current /sda1 to 100 gig (from 68 gig). Is moving right somehow better?

Would that mean resizing the /sd5 and then the /sd3? Or can that be done simultaneously?

All this somewhat reminds me of what the Old Indian said. See attached screenshot.

And thank you, again.

---

### Post by oldfred on 2013-02-09
As the Indian is saying the hard drive will not change size how every you slice it. :)

What is the real goal? 

I prefer small root partitions of 15 to 25GB and all data elsewhere. But for reliability I want an entire system on one drive but an operating system on every drive. And since I do not trust drives long term, so every couple of years I buy a new one as my main drive and lower the use, more as backup of the older drives.

I am now up to 4 drives on my 6+ year old system with XP & Ubuntu still on my original two 160GB drives, but do not boot XP. My new 62GB SSD has two Ubuntu's, my current working and the next version for testing. I also then have all data on a somewhat newer 640GB drive and many older or new test installs of Ubuntu. Every install uses the same data partitions via links.

---

### Post by Mark_in_Hollywood on 2013-02-10
I got my first PC in about 1982. I got used to DOS locking up, then Windows blowing up. First COM port incompatabilities, the Registry @#5Vd3*% then, a truly non-robust OS. How is it that Mr. Gates can sell a known defective product at a fixed price? Prior to 1984, I had a Kaypro-II and before that, a Commodore-64. Don't laugh!

So, I'm a Neanderthal in terms of modernizing to reflect the true value of what Linus Torvalds gave the world. Yet, I'm trying to learn and adapt.

I guess I believe that the newly freed 68gig should go on the end of /sda5. But, technically that's not necessary. With your help, Old Fred, I now understand that. I want to make some use of that space. I guess it can go for data, the only question is how to make it part of my current /home with links or in some other way. I guess that moving all those partitions around (back and forth) isn't such a good idea after all. Especially if the partitions can hook up with each other.

I have but one hard drive for the OS. It's a 400-gig refurbished Western Digital "enterprise class" or server grade hd with a mtbf of 1.2 million hours. In buying this drive, my first SATA, I got a real bargain at $40. S.M.A.R.T. show zero flaws or other problems after 25,000 hours of use. I will never by a non-server grade drive again.

Please point me towards a Ubuntu Doc that shows how to tie the partitions together, if you know one. Or at least give me the nomenclature to search for. 

Thanks again.

---

### Post by Bufeu on 2013-02-10
Don't mess with the partitions, it can go really bad if you do something wrong.
As OldFred said; a small root partitions of 15 to 25GB (maybe 30 GB) is recommended. Personally, I recommend to have /home, /boot and /tmp on different partitions as well. If you have an SSD you might wanna enable TRIM for Linux in fstab (I think you have to add "discard,noatime" to the mount options and then manually run *fstrim -v /path/to/mounted/ssd/partition* to enable it).

Why separate /boot and /tmp from the rest? If something goes wrong when updating the kernel or when you reconfigure GRUB, it's **much** easier to fix it if /boot is on a separate partition. The same thing with /tmp. If something does wrong there, it's easy to fix it if it's on its own partition.
If you are paranoid, make a own partition for all the folders in */*. Or just backup the data you wanna keep, e.g. with rsync or to a cloud service.

---

### Post by grahammechanical on 2013-02-10
@Mark_in_Hollywood

Hi. I am a little confused about what you want to do. Is sda1 empty? If so you can

Install Ubuntu into sda1, giving sda1 the mount point of / and sda5 the mount point of /home. During the re-install Grub will also be re-installed into the MBR of sda and it will boot the Ubuntu on sda1.

The Grub menu will also give you an option to boot Ubuntu on sda3. But you can now delete sda3. You can then shrink sda1 to about 25GB. Expand sda4 to take up all the unallocated space. Then expand sda5 to take up the unallocated space within sda4.

When I move or resize my partitions I do one action at a time. We can put in a list of actions to be performed one after another but that will take a long time to run. And I worry about things going wrong. They say it can happen. I have not experienced this. I do one action with Gparted at a time. Even re-loading the live session each time. And making sure Ubuntu still boots.

Remember, once you have deleted sda3 there will still be a listing for it in the Grub menu. To remove that item run

```
sudo update-grub
```

Regards.

---

### Post by Mark_in_Hollywood on 2013-02-10
> Why separate /boot and /tmp from the rest? If something goes wrong when updating the kernel or when you reconfigure GRUB, it's **much** easier to fix it if /boot is on a separate partition. The same thing with /tmp. If something does wrong there, it's easy to fix it if it's on its own partition.
If you are paranoid, make a own partition for all the folders in */*. Or just backup the data you wanna keep, e.g. with rsync or to a cloud service.

I have / on a separate partition (that's my /sda3 of about 15 gig). I have /home as /sda5. That's about 220 gig (less the 68 gig I'm posting here about)

What I did was to delete a partition where win-7 sat. It is now empty, has about 68 gig of free space and I'm trying to find the best solution to putting it to good use. Thanks for your input.

---

### Post by Mark_in_Hollywood on 2013-02-10
> **grahammechanical said:**
> @Mark_in_Hollywood

Hi. I am a little confused about what you want to do. Is sda1 empty? If so you can

Install Ubuntu into sda1, giving sda1 the mount point of / and sda5 the mount point of /home. During the re-install Grub will also be re-installed into the MBR of sda and it will boot the Ubuntu on sda1.

The Grub menu will also give you an option to boot Ubuntu on sda3. But you can now delete sda3. You can then shrink sda1 to about 25GB. Expand sda4 to take up all the unallocated space. Then expand sda5 to take up the unallocated space within sda4.

When I move or resize my partitions I do one action at a time. We can put in a list of actions to be performed one after another but that will take a long time to run. And I worry about things going wrong. They say it can happen. I have not experienced this. I do one action with Gparted at a time. Even re-loading the live session each time. And making sure Ubuntu still boots.

Remember, once you have deleted sda3 there will still be a listing for it in the Grub menu. To remove that item run

```
sudo update-grub
```

Regards.

Re-Posting sudo fdisk -l

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf3e1e104

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   143570943    71784448   83  Linux
/dev/sda3   *   143572905   174176729    15301912+  83  Linux
/dev/sda4       174176791   781417664   303620437    5  Extended
/dev/sda5       174176793   764420894   295122051   83  Linux
/dev/sda6       764420958   781417664     8498353+  82  Linux swap / Solaris

the /dev/sda1 is the former windows partition that Win7 used. Once I was certain I was deleting it, I expanded /sda1 into what was /sda1 and /sda2. The /sda1 had been about 100 megabytes. The /sda2 was about 68 gig. Those are the partitions that Win7 made at install time.

At your next paragraph, you say: "install Ubuntu". I have Ubuntu 12.04 LTS Precise Pangolin (3.2.0-37-generic-pae) installed on /sda3 and my /home on /sda5. I cannot see a value to a re-installation. It would require several hours of download time alone, to say nothing of re-installing all my apps, like VLC or MythTV. 

My quest is to make use of what is (now called) /sda1. It is empty. It does not even have a format, i.e., jfs, ext3, btrfs. I would like it to find /home (or the OS to know it had an extra 68 gig of space), but lacking that, I'm getting scared of copying and moving partitions around. It _seems_ that telling /etc/fstab and grub.cfg that more space is available for the the OS's use is the "less is more" option.

LASTLY, I have Deja-Dup's backup of /home. I'm uncertain as to how it can copy / (root) while the / is mounted.

---

### Post by oldfred on 2013-02-10
My shared data partition is more so I can use the same data in multiple installs. But you can link folders in a data partition if you just have one system. I created folders for all of the normal /home partition in my data partition and link them back home. You can link one or many.

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

   Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

