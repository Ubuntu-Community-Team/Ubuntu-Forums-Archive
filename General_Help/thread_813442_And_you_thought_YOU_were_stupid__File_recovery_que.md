---
title: "And you thought YOU were stupid?  File recovery question."
date: 2008-05-30
forum: General Help
---

### Post by Midnightsun on 2008-05-30
OK,

I've done some monumentally stupid things in my time, but this one takes the cake.

I had planned to reinstall Ubuntu so I thought the sensible thing to do was move (not copy - stupid like I said) my important files to another partition where I had Linux Mint installed.  I mounted the partition in ubuntu and accessed it.  Not being logged into mint I had no permissions for most folders so I assumed the tmp folder on that partition would suffice as a temporary location to put them.  Long story short, I boot into Linux Mint and go to access those files and move them to a more permenant home and discover they are gone.  After going through the stages of anger, denial etc etc, I decided one last try was to come here and ask if there was any hope at all in hell of recovering even fragments of any of them.  Not sure if they were gone because the tmp folder auto-wipes every boot or if Mint doesn't like other OS's putting stuff in it's folders but one way or another they're gone.

I realise this is probably an exercise in futility and I'm just delaying the final stage (acceptance) but I thought it was worth a shot to try...

---

### Post by Monicker on 2008-05-30
Ubuntu and Debian do clear out the tmp directory at every boot.

You can try testdisk to see if it can recover the files.

[http://ubuntuguru.wordpress.com/2007/03/15/testdisk-saves-the-day/]("http://ubuntuguru.wordpress.com/2007/03/15/testdisk-saves-the-day/")

A forum search should turn up links to other directions for using testdisk.

---

### Post by unutbu on 2008-05-30
There is a way to maybe recover some files, but no guarantees.

First, do not boot back into Linux Mint. If the Mint OS is running, it is writing to files. As it writes, it may overwrite the hard drive data that used to represent your files.

Do you have space to completely backup your Linux Mint partition? (you're going to need it).

The structure of a ext3 file system is held in superblocks. When Mint deleted your files from /tmp, it really just altered a few bits in its superblock, it did not actually wipe out all the 0's and 1's that compose your files.

What you need is a way to recover the old filesystem structure. That is, you need a way to recover the old superblock.

The first thing to do is make a complete backup image of the drive as it now stands. That means
hooking up an external hard drive, or creating an empty partition that is as large as your entire Mint partition and
dd'ing the entire contents onto the backup drive or partition. Then you do all your recovery work from the backup. I know this sounds daunting and impractical, but this is technically the best way. It depends on how serious you are about recovering your data.

Next, you have at least two options:

First, you might want to try [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") and [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec").
 
I've never used either of these, but they look promising, and is written by someone who knows a heck of a lot more about recovery than I do. Despite its name PhotoRec can recover a [wide variety of files]("http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec"), not just image files. A very  interesting feature of PhotoRec is that 
> PhotoRec ignores the filesystem and goes after the underlying data, so it will still work even if your media's filesystem has been severely damaged or re-formatted.


The second option is one that I've had personal experience with. I've managed to salvage some data from a partition I borked by doing, essentially, the following: (Below I call the backup partition sda1; we'll need to change that depending on where you make the backup).

Boot from a Linux OS (other than Mint!) and type

```
dumpe2fs /dev/sda1 | grep -i superblock
```

The output hopefully will look something like

```
Primary superblock at 0, Group descriptors at 1-1
Backup superblock at 32768, Group descriptors at 32769-32769
Backup superblock at 98304, Group descriptors at 98305-98305
Backup superblock at 163840, Group descriptors at 163841-163841
Backup superblock at 229376, Group descriptors at 229377-229377
Backup superblock at 294912, Group descriptors at 294913-294913

```
Then you run
```
fsck -b <superblock> /dev/sda1
```

where you replace <superblock> with the superblock number you found above (e.g. 32768, 98304, 163840, 229376, etc.)

fsck will try to recover the old filesystem using the old superblock whose location you provided.
The old filesystem hopefully still remembers what the file system looked like when your files were in /tmp. 

You then mount /dev/sda1 and look for your files (or what's left of them) in /tmp or /lost+found.

Post here if you have any questions, I'll try to answer them the best I can.

Best wishes and good luck.

---

### Post by Midnightsun on 2008-06-03
Hey guys,

Thanks for the replies.  Sorry for the late response but I've been out of town for a few days.

I attempted to use testdisk to identify the missing files but no amount of scanning was able to reveal them.  Thankfully, I remembered that I had previously saved some of the most important data previously on a flash drive so all I really lost was my movie/tv collection which is replaceable eventually.

Thanks again for the help.  I can safely say this is one mistake I will not be making again.

---

