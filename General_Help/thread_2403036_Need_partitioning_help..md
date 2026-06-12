---
title: "Need partitioning help."
date: 2018-10-06
forum: General Help
---

### Post by hiloguy on 2018-10-06
I finally managed to do a fresh install of 18.04 on the second HDD in my laptop, but I assumed the install would delete all the old partitions as it installed.  I went with regular install; not "something other."  Now I have this:
[ATTACH=CONFIG]281270[/ATTACH]
The "key" symbols also appear in the same places when I opened GParted from a live-usb boot.  It said a portion of those partitions are in use.

Is there any way I can move the HOME folder into the unused 400 Gb partition?  Failing that, can I somehow delete the partitions and just utilize the whole 500 Gb drive as if I had formatted it before the install?  Or any other suggestions other than starting from scratch with another fresh install?  I've spent a long time installing and configuring this install and would love to be able to keep it!

Thank you!

---

### Post by ajgreeny on 2018-10-06
You have many partitions for your Ubuntu install as logical partitions sitting inside an extended partition, /dev/sdb2, including a swap partition.

That swap will be found and used automatically even by a live system so to make any changes you will have to turn swap off by right clicking in gparted on /dev/sdb6 and choosing swapoff.  You may also need to right click on all other partitions with the key icon showing, one by one, and chose unmount.  Once all are unmounted you should be able to work on them.

However, you do not give us many details of exactly what you want; the only partition of 400GB is that extended partition sdb2, which could be made larger by the 37.25GB of unallocated space between sdb1 and sdb2.  I assume that your /home is currently a folder in the root partition, not a separate partition, so we would have to find a way to copy all your current home data files to the new /home partition which could be difficult unless you can copy all of home to an external backup (which you should do regularly).

An old thread about doing this is at [https://askubuntu.com/questions/643441/how-to-create-a-separate-home-partition-after-installing-ubuntu-under-single-p](https://askubuntu.com/questions/643441/how-to-create-a-separate-home-partition-after-installing-ubuntu-under-single-p)
and a community help page at [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

What is actually on that large sdb5 partition at present; is it just data files which would normally be within your /home anyway as that might make the job a bit easier?

---

### Post by Dennis N on 2018-10-06
I don't see the unused partition. Of the ext4 partitions, your root file system is on sdb7 and something is using 231 GiB of sdb5.

---

### Post by hiloguy on 2018-10-06
OK< what I started out to do was to do a simple, "regular" clean install of 18.04 on my 500 Gb HDD (in the optical drive adapter).  I assumed using the regular (as opposed to "something esle" install, the HDD would be formatted in the process and all the old partitions deleted.  Not!  So what I want at this point is to just get back to simple, if that's possible from here.  You asked what was on that 400 GB partition,  How do I see what is actually on each of those partitions?  The only reason I knew something was amiss was when I was loading my photo files back into "Pictures" and was told, "not enough room."  So evidently the entire OS loaded into one of the tiny partitions?  I don't know how to show what is in each of the partitions.

So . . . can I simply delete any of the existing partitions that are empty?  I would be happy to delete all my personal files, as they are easy to reinstall from my backup drive.  I would prefer to not have to reinstall Ubuntu since I spent a long time configuring everything the way I want it.  It was all working sweetly until I got that "not enough room" message!

If I can delete partitions and just let Ubuntu use up all the space it wants like a regular basic install, How do I see what's in each partition so I delete only my data and photo folders?

---

### Post by hiloguy on 2018-10-06
Another option here to keep things simple for this many-year Ubuntu user who still has trouble with the inner workings:  As much as I don't want to have to spend the time necessary to reconfigure another fresh install of 18.04, I'm willing to do it if I have to.  To that end, I need to know this:  If I format the second HDD in my optical drive bay for the exclusive use of 18.04, how do I make sure that it gets installed on that HDD in the install process?  I don't really care about assigning special partitions, as I've always had good luck letting Ubuntu install itself without entering "something else."  I just need to know that I'm not going to jeopardize the 125 Gb SSD that W7 is on.

Thank you!!!

---

### Post by Dennis N on 2018-10-07
I think your entire Ubuntu install is on /dev/sdb7. It is a reasonable size: 40 GiB. I regularly do installs with 20-25 GiB, but I also have a data partition to store big groups of files such as my music files and my camera images. This relieves the space demands on the partition I installed Ubuntu on.

I mount the data partition at startup by putting a line to do it in the file /etc/fstab, which specifies file systems and partitions to be mounted when I boot the system.

After setting up the data partition, I can access it from the file manager - to make it quicker, I bookmark commonly used folders in the data partition (camera, music, etc).

If sdb5 on your picture is available (right now it shows 231 GiB in use) it would make a good data partition. It would be simple to set up if that stuff on there is expendable.

(comment: not really important, but I also don't see what sdb1 is doing - probably nothing since its not mounted according to the screenshot. Could be an artifact of previous install?).

---

### Post by hiloguy on 2018-10-07
Thank you for your reply!  **So how can I see what files are now in the various partitions?**  What I think would solve my problem is if I could simply move my Home folder into that empty 400 GB partition.  But how do I do that?

You asked what is is in sdb1; that's the main 125 Gb SSD that has W7 on it for those few times when I need W7, like for udating a GPS, etc.  The 500 Gb drive installed in an optical-bay adapter is exclusively for 18.04.

So can you walk me through moving my Home folder into sdb2, the empty (I think) 427 Gb partition?

---

### Post by Yellow Pasque on 2018-10-08
> **hiloguy said:**
> Thank you for your reply!  **So how can I see what files are now in the various partitions?** 
They look like unencrypted ext4 partitions, so you should be able to easily mount them (using file manager or command line or whatever you like) and look.

> You asked what is is in sdb1; that's the main 125 Gb SSD

No, that would be a different disk (not sdb). Look at the picture. sdb1 is the first partition (only 1GB large). It's almost certainly a leftover separate /boot partition from the previous install.

> So can you walk me through moving my Home folder into sdb2, the empty (I think) 427 Gb partition?

It's not empty. Look at the picture (231GB used). You probably already have your photos and other media loaded in there. You may not have to move the entire home folder. You can just create a symlink(s) to the various things in there. I keep my music/vids in folders in a separate large data partition and make symlinks. That way I don't need to have a separate /home partition and I can access the data from other Linux installs.

---

### Post by ajgreeny on 2018-10-08
> **hiloguy said:**
> Thank you for your reply!  **So how can I see what files are now in the various partitions?**  What I think would solve my problem is if I could simply move my Home folder into that empty 400 GB partition.  But how do I do that?

You asked what is is in sdb1; that's the main 125 Gb SSD that has W7 on it for those few times when I need W7, like for udating a GPS, etc.  The 500 Gb drive installed in an optical-bay adapter is exclusively for 18.04.

**So can you walk me through moving my Home folder into sdb2, the empty (I think) 427 Gb partition?**
You do  not have an empty 427GB partition; that is the extended partition that contains the other partitions so it is like a wrapper round all the others; see my comments in post #2.

It may be possible to put your home onto the 372GB sdb5 but that is already about two thirds used so we really need to know what is there; is it your data files for Ubuntu?  It is certainly nothing to do with Windows as it is an ext4 partition, not readable by Windows so all those 231GB are from your Ubuntu.
It may help us if you could still boot to this Ubuntu install and from there run terminal commands ```
df =hT
sudo parted -l
mount
``` one by one and show us the output of each here.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by hiloguy on 2018-10-08
Well, I REALLY appreciate all the assistance from everyone in this thread, but for me the fixes just kept getting more and more complicated.  So I did what I probably should have done as soon as I realized that I had tried to install 18.04 onto a HDD that had been partitioned for a previous install.  I kinda figured (hoped?) that Ubuntu would install into the old partitions, using them the way 14.04 had done.  Not happening, so the whole new install went into a tiny partition and then when I started loading my files from backup, I got the "not enough room" message.  

So last night, I deleted all of the partitions on my second HDD (W7 in on the main 125Gb SSD) and started over with another clean install letting Ubuntu use the whole drive.  Maybe one day when I feel brave enough to deal with it, I'll try moving my Home folder into a separate partition.  But for now, everything is working sweetly. Both OS's boot properly, and I really like 18.04.

Thanks again, everyone!

---

### Post by rainintheface on 2018-10-08
For what it is worth, I have successfully installed numerous Linux distros on a two-drive PC (one HDD and one SSD). I have found that for me, a somewhat technical person with limited patience, that the best approach is to first reformat the drive I want the new install of Linux (in my case Ubuntu) on. I typically use GParted if I am moving from one Linux distro to another. I keep a copy of GParted handy on a CD so that I can boot into it and reformat drives even if the operating system isn't right or I want to reformat the drive the OS is located on. Format the entire drive as ext4. I then turn off the computer. Disconnect the second drive, which in my case is the HDD that I just use as a storage drive. I then boot up the new install disk or USB stick and choose to do a regular replace and install on the only disk that shows. This allows Ubuntu, or whatever distro I am using, to properly install itself without dealing with partitions, etc. left over from the previous install. Luckily on my PC, which is homemade and in a large case, it is a matter of maybe two minutes to open up the case and unplug one of the drives. This approach saves a lot of hassle, though I know it won't work for everyone.

---

### Post by ubontik2 on 2018-10-11
On laptop I have 1 TB hard drive. I installed Ubuntu-Studio. I want to create a partition but when I do it with Gparted it does not allow me. I noticed there is a key sign.

---

### Post by Yellow Pasque on 2018-10-11
> **ubontik2 said:**
> On laptop I have 1 TB hard drive. I installed Ubuntu-Studio. I want to create a partition but when I do it with Gparted it does not allow me.

Giving a screenshot like the OP did would help. Either that, or give more detail on what exactly you are trying to do and give output of parted command.
```
sudo parted -l
```

>  I noticed there is a key sign.

That means the partition is mounted, so you can't alter it.

---

### Post by ubontik2 on 2018-10-11
$ sudo parted -l

Model: ATA TOSHIBA MQ04ABF1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

---------------------
Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
 2      538MB   1000GB  1000GB  ext4
---------------------
I want to shrink #2 to 60-70 GB and create a FAT32 primary partition.
Will it be easier to wipe out, create partitions, and install Ubuntu and Windows on other partition?

---

### Post by hiloguy on 2018-10-11
No expert here, but if you read the ongoing posts above in which I had similar issues, It got so far over my head that I finally solved my problem and took the coward's way out!  I deleted all of the partitions, making one big empty space out of my second HDD, then installed 18.04 from scratch.  Worked like a charm, but of course I had to re-install all my personal files.  That took a while, but at least it was predictable to a good outcome.  I've had similar issues with half a dozen laptops and even with a single HDD, I always install Windows first and then reboot to the USB Ubuntu install.  Then I can either use "Something else" option that allows me to create a HOME folder.  But on most of them, I let Ubuntu just go ahead and use the space it needs.  The only issue I've ever had with doing it that was was having to reinstall my personal data if I ever needed to redo or upgrade Ubuntu.

There are lots of good folks here who will tell you better ways to do all this; again, I'm no Ubuntu expert, just a guy who's been using it since 8.04 and (mostly) loving it all the way along!

---

### Post by ubontik2 on 2018-10-11
Thanks for reply. I think if I install windows first it will boot from the Windows. I want to boot from Ubuntu by default because I use Windows probably a couple times a month or less.

---

### Post by hiloguy on 2018-10-12
Yeah, I hardly ever use Windows.  The standard default Ubuntu install boots to Ubunty by default.   Upon boot-up, you get a small menu for a few seconds that allows you to boot into Windows if you choose.  You can simply click ENTER and it will immediately boot to Ubuntu, or just ignore the menu and it will boot into Ubuntu in a few seconds by default.  There!  Problem solved!  (I love Ubuntu.)

---

### Post by vidtek on 2018-10-12
Hilo-

You sorted your problem by reformatting, probably the best way to go from the mess of partitions you had.

If in future you are making changes to your installation-for instance doing a dist-upgrade take a 1/2 hour or so to do a backup.

Install qt5-fsarchiver, I think it is in the repos now, otherwise google and add the repo to your system.

Here is the gui interface, it's pretty straightforward:-[ATTACH=CONFIG]281320[/ATTACH]

It has many capabilities, it can do a "live" backup of your system partition while you are using it.  For the system partition always make sure you 
include the pbr option.  UEFI, MBR systems all linux formats and fat32 as well are catered for with this programme.  You don't have to use the gui, there is a command-line version in the repos just called fs-archiver.  Here is a sample of the backups I use:```
To save the sda2 partition to /data/backup/ultimate.fsa file

Boot from a live cd/pendrive with SystemrescueCD

first create mount directory (this is for my system, yours will have different drive mappings find them with[CODE]blkid
``` 

mkdir /mnt/data

mount the backup partition/folder

mount /dev/sda4 /mnt/data

then run

fsarchiver savefs /mnt/data/backup/ult2-9-12-2017.fsa /dev/sda6 -v -j8      # the -v gives a sreen output of what is happening, and the -j8 means it uses all 8 cores of the cpu-change it to suit your hardware. 

to restore:

first mount the backup partition/folder

mount /dev/sda4 /mnt/data

then run

fsarchiver restfs /media/mint/data/backup/ult1-9-12-2017.fsa id=0,dest=/dev/sdb6 -v -j8

 
Take a look at fsarchiver

It can be found on the latest SystemRescueCD

Reportedly made by the same guy who authored partimage.

It sports a lot of improvements including: - ext4 support - ntfs support - file-level instead of block-level - compression using multiple cores

Basically, after a partition is saved/compressed it can be restored to different size partitions, and partitions of different formats (so you can use it to convert a partition's format too), and if part of the backup gets corrupted it doesn't destroy the whole image (like it would on a block-level backup.

Tthe id=0 is necessary because an image can contain multiple partitions. For more directions on usage (such as saving multiple partitions) checkout the QuickStart guide.

[/CODE]

I do a backup before I make any system changes, it is so easy to roll back to a previous install, a bit like Windows system restore only better.

I usually do a backup of my home partition too at the same time.

Another neat feature is the ability to restore to a smaller or bigger partition size.

Only thing, when restoring a system partition you need to do it from a live dvd/pendrive boot media.  I use system rescue disk available from sourceforge.

Here is a screenshot from Dolphin file manager of my recent backups.
[ATTACH=CONFIG]281321[/ATTACH]

I hope this will encourage you to make changes and when you mess it up-as you will we all do-it is easy to revert.

Cheers, Tony.

---

### Post by hiloguy on 2018-10-12
When I'm about to re-install Ubuntu for an ugrade or any other reason, I always just start a backup of everything in my Home folder to an external drive.  I start it and go away for a few hours and when I come back, it's done.  Actually, I do a redundant backup to Dropbox, as well, just in case.  Then when my new OS is all installed and configured the way I like it, I load all that stuff back into the Home folder and I'm good to go.  That way I don't need to mess around with any commands into Terminal.  Probably not the best way to go, but for those of us who love using Ubuntu on a daily basis as I have for many years, it's easy and pretty much bulletproof.  To me, learning the cryptic inner workings of Ubuntu is akin to when I was in Junior High some 70+ years ago and trying to learn algebra!  I can follow specific instructions I get on this terrific Forum for making changes/repairs in Terminal, but I have no clue as to why any of it works . . . or often doesn't!

Thanks to everybody on this Forum for their dedicated assistance, especially to folks like me.  I know it's hard to be patient sometimes, but you always are!  :)

---

### Post by ajgreeny on 2018-10-12
> **ubontik2 said:**
> On laptop I have 1 TB hard drive. I installed Ubuntu-Studio. I want to create a partition but when I do it with Gparted it does not allow me. I noticed there is a key sign.
Please do not hijack someone else's thread assuming your problem is the same and can be solved the same way; very often that is not so, and it is often very confusing for all concerned, including you, the hijacker.

If you find yourself in this situation again please create a new thread, possibly showing a link to the one you believe is the same problem so that you can get the full support and attention to your specific problem.

---

