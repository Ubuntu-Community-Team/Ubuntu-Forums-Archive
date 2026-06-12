---
title: "HDD suddenly full, some random files damaged; I can't boot up Ubuntu"
date: 2015-03-21
forum: General Help
---

### Post by i21032015 on 2015-03-21
Everything was going perfectly and the computer began going slow, to the point that I was thinking about restarting the computer. So, suddenly, I couldn't save a text file because the Hard Drive Disk was full. I checked, and the system said that there were 0 bytes left.

I rebooted the computer, thinking that it was just some bug and I couldn't load the desktop or do anything other than move the mouse around the screen. I had to shut it down with the power button.

I tried running a live USB version of the OS. It loaded without problems. Then, I checked some random files and directories. Some were intact, while others were damaged.

I guess there was some probem and that random data was written to the disk until it was full. But I don't know. What happened? How can I solve this?

Edit: booting in recovery mode doesn't work either.

---

### Post by dino99 on 2015-03-21
boot on usb, then run 'fsck' on the damaged partition

---

### Post by pmi2 on 2015-03-21
> **i21032015 said:**
> ...What happened? How can I solve this?From personal experience, ;),  try to save at least your important files BEFORE you do anything to try to solve the problem.  For example, if you can boot from a live USB, save your Home directory on a different USB, or a DVD-RW, or whatever you have available.  Makes the job of getting back to a running system so much easier later.

---

### Post by i21032015 on 2015-03-21
> **9d9 said:**
> boot on usb, then run 'fsck' on the damaged partition
I'm afraid I will do something dumb. I typed:
```
fsck UUID=845ac... -V
```
where 845ac... is a 36 chars long string, including 4 dashes, that's associated to the partition that was damaged.

I don't know much about linux. I installed it recently. I have also ran away from these situations as much as possible, so right now I'm clueless about what I have to do. When I ran that command, the next appeared:
```
fsck from util-linux 2.20.1
[/sbin/fsck.ext2 (1) -- /dev/sda5] fsck.ext2 /dev/sda5
e2fsck 1.42.8 (20-Jun-2013)
/dev/sda5 is mounted.



WARNING!!! The filesystem is mounted. If you continue you ***WILL*** cause ***SEVERE*** filesystem damage.


Do you really want to continue<n>? no
check aborted.
```

So, what do I do?

---

### Post by pmi2 on 2015-03-21
There is probably no reason to have to use that long string, /dev/sda5 (or whatever the number of the partition) should work.

Don't run fsck on a mounted partition, that is what that error is telling you.  Bad things could happen.
Before you run fsck, unmount the partition first.

Look up what some of the options mean, for example, -v(verbose), -n(make no changes) I always use this first before I try to fix anything, -f(force checking) in other words run fsck even if the partition looks clean. Avoid using -p unless you know exactly what you intend to happen.

Examples:

 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list

Here is an example of fsck run on one unmounted partition w. no errors (well, the day is still young here, :D ):
> peter@Flattop:~$ sudo fsck /dev/sda6 -n -v -f
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      216407 inodes used (5.87%, out of 3686400)
         543 non-contiguous files (0.3%)
         196 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 182872/140/1
     2680819 blocks used (18.18%, out of 14744576)
           0 bad blocks
           1 large file

      163515 regular files
       18194 directories
          57 character device files
          25 block device files
           0 fifos
          10 links
       34606 symbolic links (33303 fast symbolic links)
           1 socket
------------
      216408 files
peter@Flattop:~$ 
In other words, unmount the partition, run fsck with the -n option and whatever other options you like, then decide what you want to do next.  Best of luck.

---

### Post by i21032015 on 2015-03-21
> **pmi2 said:**
> There is probably no reason to have to use that long string, /dev/sda5 (or whatever the number of the partition) should work.

Don't run fsck on a mounted partition, that is what that error is telling you.  Bad things could happen.
Before you run fsck, unmount the partition first.

Look up what some of the options mean, for example, -v(verbose), -n(make no changes) I always use this first before I try to fix anything, -f(force checking) in other words run fsck even if the partition looks clean. Avoid using -p unless you know exactly what you intend to happen.

Examples:

 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list

Here is an example of fsck run on one unmounted partition w. no errors (well, the day is still young here, :D ):

In other words, unmount the partition, run fsck with the -n option and whatever other options you like, then decide what you want to do next.  Best of luck.
Thanks. It said: /dev/sda5: 553488/2191168 files (0.2% non-contiguous), 8315551/8757504 blocks
though, nothing else happened and I still see damaged files. I don't know if it did anything. I passed the -f parameter and I wasn't asked anything.

---

### Post by pmi2 on 2015-03-21
If you used the -n option the first time, did you run it again without the -n, to see if anything happens?

And, what exactly do you mean by "damaged" files?

edit:

more info about using fsck, here: [https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

---

### Post by i21032015 on 2015-03-21
> **pmi2 said:**
> If you used the -n option the first time, did you run it again without the -n, to see if anything happens?

And, what exactly do you mean by "damaged" files?

edit:

more info about using fsck, here: [https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)
Oh sorry, it didn't say anything else because I was using -V instead of -v.
Whether I use -n or not doesn't change the output in the slightest. It shows a list of information such as"553488 inodes used" and "410124 regular files". I could write it all, but I'm (forcefully) writing this on a mobile. It says "0 bad blocks", if that's important.

By damaged, I mean that some files can't be read/written and attempting it generates an error. There are some system directories that act like this, which I guess is why the OS doesn't boot up.

---

### Post by pmi2 on 2015-03-21
Saving your work-in-progress, and any other files that are important to you should be the priority now.  If you still have your bootable USB stick/thmb drive, there is a good chance you can boot from there, navigate to your home directory or anywhere else you have stored your data, and make a copy.  i think you can make a copy to the same USB device if necessary, but a separate media is preferrable.

Hard to know what may be happening to your files, since you can't very well paste the errors (or can you, if you boot from a live media?)

---

### Post by i21032015 on 2015-03-21
> **pmi2 said:**
> Saving your work-in-progress, and any other files that are important to you should be the priority now.  If you still have your bootable USB stick/thmb drive, there is a good chance you can boot from there, navigate to your home directory or anywhere else you have stored your data, and make a copy.  i think you can make a copy to the same USB device if necessary, but a separate media is preferrable.

Hard to know what may be happening to your files, since you can't very well paste the errors (or can you, if you boot from a live media?)
I made sure to copy everything before I opened this thread.
I am booting from a live usb, but I can't connect to the internet from my computer for other reasons.
I will just write it letter by letter:
```
(Passes 1 to 5)

553488 inodes used (25.26% out of 2191168)
306 non-contiguous files (0.1%)
595 non-contiguous directories (0.1%)
# of inodes with ind/dind/tind blocks: 0/0/0
Extent depth histogram: 499349/154/2
8315551 blocks used (94.95% out of 8757504)
0 bad blocks
3 large files

410124 regular files
79441 directories
57 character device files
25 block device files
0 fifos
26 links
63832 symbolic links (53893 fast symbolic links)
0 sockets
------------
553505 files
```

---

### Post by pmi2 on 2015-03-21
I see more than twice as many files on your system as on mine, and four times as many directories.  That seems odd, unless you know you download or created those for some specific reason.  Beyond that, it looks ok.

I would probably check the size of the home directory, and the browser directory (in my case that is ~/.mozilla and I have around 100 files there).  You could check all subdirectories in the Home directory.  Beyond that I don't know.

---

### Post by i21032015 on 2015-03-21
> **pmi2 said:**
> I see more than twice as many files on your system as on mine, and four times as many directories.  That seems odd, unless you know you download or created those for some specific reason.  Beyond that, it looks ok.

I would probably check the size of the home directory, and the browser directory (in my case that is ~/.mozilla and I have around 100 files there).  You could check all subdirectories in the Home directory.  Beyond that I don't know.

well the problem began when I suddenly ran out of memory, when I had 50% of my HDD unused yesterday. Perhaps some file kept copying itself or something?

Could I just reinstall the OS? I can't find a better solution.

---

### Post by pmi2 on 2015-03-21
> **i21032015 said:**
> ...Could I just reinstall the OS? I can't find a better solution.Sure, you can always just reinstall the OS.  If you do that, make sure you format the disk (or the partition) when you reinstall.  It would have been nice to know what app caused such a large number of files to just appear within a day, so you can avoid it in the future, but it may not be worth the time playing detective.

---

### Post by bardo2 on 2015-03-22
Hi,
Heads up... been there, done that, recovered from it, like so:
Boot up from live CD to have a system working from RAM and CD only and INSPECT the drive contents to find the cause for the vanishing space. (In my case, there had been logfiles exploding to be Gigabytes in size whithout me noticing it (files were in /var/log and in /home/<myuser>). Look at those to see, whats been causing it, then compress or delete those and your system might restart with ease, where further action to prevent future hickups might be necessary. At least for me the most difficult part was to identify the file growing in size inadvertedly. DIsk analyser (baobab) can be your friend!

---

### Post by i21032015 on 2015-03-30
> **bardo2 said:**
> Hi,
Heads up... been there, done that, recovered from it, like so:
Boot up from live CD to have a system working from RAM and CD only and INSPECT the drive contents to find the cause for the vanishing space. (In my case, there had been logfiles exploding to be Gigabytes in size whithout me noticing it (files were in /var/log and in /home/<myuser>). Look at those to see, whats been causing it, then compress or delete those and your system might restart with ease, where further action to prevent future hickups might be necessary. At least for me the most difficult part was to identify the file growing in size inadvertedly. DIsk analyser (baobab) can be your friend!
Hello, sorry for the late reply.
running sudo du -sx /* | sort -n shows, among other things, this:
2359539 /rofs
5206376 /cdrom
I don't even know what those directories are, but they're apparently huge. I tried to see how much space cdrom occupies through the GUI and it says it occupies 0 bytes, and there's apparently nothing inside. However, if I select all the other dirs in /, they don't even measure half of the disk space used. About /rofs, I can't even find it.

Edit: I tried sudo du -sx /rofs/* | sort -n and realized that only through the GUI can't I see that dir. This might be important:
247565 /rofs/lib
276442 /rofs/var
[1798229]("tel:1798229") /rofs/usr
Also /rofs looks like a copy of / with some things missing??

sudo du -sx /cdrom/* | sort -n:
156712 /cdrom/VirtualBox
849432 /cdrom/casper
4188160 /cdrom/casper-rw


Finally I tried:
> cd /cdrom
> ls -l
and saw:
-rwxr-xr-x 1 root root 4288675840 Mar 30 13:24 casper-rw

I don't really understand any of this. But "Mar 30 13:24" was minutes ago.
Also once I solve this I'd like to learn to use these commands. Is there a book that you would recommend me? I don't want to go off-topic though.

---

### Post by bardo2 on 2015-03-30
your results were to be expected. From inside the live OS you were seeing the contents of the ramdisk + live iso image, not the contents of your disk (yet).
well, if you analyse from withing the live filesystem, there are cdrom and a virtual / (really residing in RAM). dont bother with those. you have to mount your OS partition and analyse that one instead

[LIST]
[*]create a directory to mount the os
[*]identify os partition
[*]mount it there
[*]begin analysis of subtree only
[/LIST]

---

