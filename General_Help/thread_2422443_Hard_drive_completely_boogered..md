---
title: "Hard drive completely boogered?."
date: 2019-07-07
forum: General Help
---

### Post by Gnusboy on 2019-07-07
Of all the goofy problems I've had with Ubuntu, I think this is the worst. If it's solvable I'd really like help.
Ubuntu 16.04

The 650GB hard drive has 4 volumes:
A)  113 GB volume 49.8 GB used out of 110 GB
B)  194 GB volume 106.9 GB out of 190.6 GB
C) 91.8 GB volume 14.9 GB out of 91.8 GB
There's an additional 156 GB unformatted partition on the 650 GB drive.

I also have a 1TB external drive with two formatted partitions - 462GB and 537GB.

About a week ago I was cleaning up some loose ends following a fix for an "out of space" error message from a few weeks ago. I'd been using Deja Dup to attempt backups, but it was fluky and seldom worked properly. Deja Dup has caused me a lot of trouble through the years. Sometimes it worked as it should, but not always. It didn't  work this time either.

With help from Kpatz and CatKiller, we figured out that through the years, the backups I  was able to complete were saved in the 93 GB boot partition. As we went through the process of moving files and creating enough space to to fix the out of space problem, I learned that I had saved the files on a boot partition that was now 97% full. 

At first it didn't matter because it was a large volume. I had never found a reason to  look through, or reinstall any of the saved backups. Now there were more than 70 backup  files and they just sat there taking up space. Getting rid of a couple of files opened  up room I could use to stabilize my system. One of the things recommended was to make a full backup of my home  folder and save it to the external drive. 

To finish the process, I needed to move or delete the all old backups and then start fresh with a full backup. I was trying to move the old files over to the external drive. I wanted to look at one of the files to see if it contained all of the  material it was supposed to have. I was not able to open the file so I went back to moving the files. I moved a couple of them without a problem, but something went very wrong. My entire system froze to a black screen. The power was on, but nothing else worked. I couldn't get a GUI or a command prompt but it did not respond to any command. 

After futzing with it I got concerned that doing something I did not understand could brick my entire computer. At the least, I had hoped to find  a way to unmount the external drive to protect the data and to possibly correct the problem. I again let it settle for a day to see if the system was broken again or just running very slow. 

I did not know what to do, so I went for the soft reboot. As it came back on the boot process looked normal. Once back on, the screen was still black, but it showed several errors in the system, followed by "initramfs"  at what looked like a terminal command prompt with a notation to enter "help." 

A screen came up with over 100 single word commands. I tried entering a few, but nothing happened. There was no prompt or indication it was working. I've spent a week looking for a workable fix, but can't find anything I  could understand well enough to be confident using to fix the problem.

So that's where I am today. I'm using one of my other computers top search for a way to fix this problem but most didn't seem to fit. One solution I found called for using a Ubuntu 16.04 disk to evaluate the situation. With so many partitions on my 650GB hard drive and the TB external drive, I'm hesitant to try it without knowing possible outcomes or dangers.

For the past week I've looked for something to describe the problem  without luck. I kept it running for 5 days because I thought a reboot  would make it worse.  A couple of days ago, it completely locked up, so I tried a soft boot.
It seemed boot, but only to a black screen. I don't recall what I did, but a message showed this info:


==========================================================================================

[   2.305853] ata1:softreset failed (device not ready)
[   2.309844] ata3:softreset failed (device not ready)
/dev/sda9: recovering journal
/dev/sda9 contains a file system with errors, check forced.
Inodes that were part of a corrupted orphan linked list found.
/dev/sda9: UNEXPECTED INCONSISTENCY;RUN fsck MANUALLY. (i.e., without -a or -p options)
fsck exited with status code 4
The roty filesystem on /dev/sda9 requires a manual fsck

BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1.4) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) help
built-in commands:
------------------
. : [ alias break cd chdir command continue followed by 120 words etc.

I tried some of the commands on the list, but they just brought me back to the initramfs prompt.

I have no idea how to continue. I've been worried that one more bad entry would brick my system.

So, can anyone help get things back on track?

---

### Post by oldfred on 2019-07-07
Have you tried booting into recovery mode? Second entry in grub menu?

Then run full fsck on all ext4 partitions. Example only shows a sdb1 which may not even be one of your ext4 partitions.
       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

If you do not understand and then able to recover from backup, then it is not a backup.
Years ago, back with floppy drives when bits were expensive, I backed up with compressed data to floppy drive. Of course compression code was area of floppy that failed and data was essentially not recoverable. Since I do not really have a lot of data, I do not compress nor encrypt my data. But it also is only local, not in some Cloud who knows where. I use rsync & copy to multiple places & sometimes copy to DVD the most critical data.

---

### Post by CatKiller on 2019-07-08
The busybox shell is for when the boot process doesn't know how to proceed any further; normally because it can't find the next step, or because something is misconfigured. It is *very* limited in what it can do, and how user-friendly it can be: if your computer was in a state to load more things and expansive helpers it would have been able to boot normally.

However, there *is* a means that has all the infrastructure to boot into a lovely environment that has all kinds of useful tools: the install image. Boot into that and you'll be able to run fsck and whatever else you need on your drives. You'll also be able to use chroot to make configuration changes to your install while in the comfortable and supportive desktop environment. With a browser to hand, too. 

You'll find it much easier to do things there than in busybox.

---

### Post by Gnusboy on 2019-07-10
Hey CatKiller

I'm looking through the suggestions by you and Fred. One question: You mentioned the install image, is that on the 16.04 disk? Is it better to just boot into that disk and go through full install process, then run the fsck and other procedures?
If I don't do a scratch install, and instead do the (try it out) mode, can I make repairs from there, and will they take permanent effect afterward?

Also, as soon as I get control of the system, should I disconnect the external drive? I don't know how much of my data made it over to there.
I suspect that at some point I could (will) lose some of my important files and become (enraged / suicidal / both). 
If I have enough fragments I can probably reconstruct the important stuff, but it would not be as much fun as it sounds.

P.S. My cat just saw your handle is got really pissed off. She says that if that try anything like that around her, she will put you into Intensive Care for a long, long time.

---

### Post by oldfred on 2019-07-10
Best to only work from live installer.
If you reinstall, that may overwrite something you have not yet recovered? 
Not sure if same drive/partition as where your data is/was?

       May be best to see details, use ppa version with your live installer (2nd option),  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by CatKiller on 2019-07-11
> **Gnusboy said:**
> Hey CatKiller

I'm looking through the suggestions by you and Fred. One question: You mentioned the install image, is that on the 16.04 disk? Is it better to just boot into that disk and go through full install process, then run the fsck and other procedures?
If I don't do a scratch install, and instead do the (try it out) mode, can I make repairs from there, and will they take permanent effect afterward?

The install disc, but not to install. The Try Ubuntu option is a fully-functional Ubuntu environment. It's familiar and easy to use in exactly the ways that BusyBox isn't.

You can run fsck, move things around, check things on the Internet, all the useful stuff. chroot will let you do things to your actual install while still using the support structure of the live environment should you need to. It sets up a virtual / for any commands that you run to your mount point. 

As oldfred says, there are also more specialised tools that might help, too. The boot repair disc provides lots of detailed information.

---

### Post by Gnusboy on 2019-07-11
I only read down to the part where your message said to boot into the recovery mode [COLOR=#000000]Then run ... [/COLOR][COLOR=#000000]full fsck on all ext 4 partitions.
[/COLOR]
I didn't see the rest ... "[COLOR=#000000]Example only shows a sdb1 which may not even be one of your ext4 partitions.[/COLOR]
[COLOR=#000000]To see all the ext4 partitions
[/COLOR]
[COLOR=#000000]sudo parted -l "

SI have 7 partitions, since at least two of those partitions are on the external drive should I remove that first?

So I started running fsck and the system started showing line after line for clearing Inodes   i.e. 

394179  is in use, but has dtime set. Fix <Y>
    "       has magic flag set.  Clear <y> 
    "       has extra size (65534) which is invalid
    "      compression flag set on file system without compression support
    "      INDEX_FL set but is not a directory. Clear HTree index
    "      I_size is 18446744073709551615, should be zero.
    "      I_blocks is 281474976710655, should be zero
    
And this repeats in sequence but with different Inodes. It appears that these lines will continue through all of the Inodes on all of the partitions until they are all repaired. Do I just hit <Yes> and keep going to the end?

Can I exit this and go back and then follow your directions?
I've been wrapped around the axle trying to get this problem solved, it's hard to pay attention.









[/COLOR]

---

### Post by oldfred on 2019-07-11
Is that a ext4 partition that you are running it on?
You run it only on ext family of formats like ext2, ext3 or ext4 or else it may cause other issues. Never run on a a drive like sdb or sda.

The first command should not be asking for y, can second automates the y answer.

---

### Post by Gnusboy on 2019-07-12
CatKiller
Oldfred

I don't know if this info is relevant:

I did an exit and a reboot and got an initramfs prompt, then an F10. I was trying to get a command to move to the top of the screen. I wanted to look through all that showed since I started this effort. F 10 didn't work and it returned [21~:   This was "not found" and I did an exit.
Rebooted and this showed. 
[      7.1.176989] sd 6:0:0:0: [sdb] Attached SCSI disk [21~:
 /bin/sh: [21~ not found
(initramfs) Exit

Begin: will now check root file system ... fsck from util-linux 2.27.1
[/sbin/fsck.EXT4 (1) -- /dev/sda9] fsck.EXT4 -a -CO /dev/sda9
/dev/sda9 contains a file system with errors, check forced. /dev/sda9:
Inode 394177 has magic flag set.
/dev/sda9: UNEXPECTED INCONSISTENCY ; RUN fsck MANUALLY. (i.e., without -a or -p opitions)
fsck exited with status code 4 done.
Failure: file system check of the root filesystem failed
The root filesystem on /dev/sda9 requires a manual fsck
(initramfs) 

Just passing it along in case it's not the best way to handle the problems.

---

### Post by CatKiller on 2019-07-12
> **Gnusboy said:**
> Just passing it along in case it's not the best way to handle the problems.

Well... no. It's not.

A live environment is infinitely more capable and easy to use than where you're trying to blindly fiddle with things. I really don't know how I could have made that any clearer.

All of the instructions for how to fix your computer were to be run from a live environment, with the single exception of oldfred's "Have you tried booting into recovery mode? Second entry in grub menu?" to which the answer appears to be "my computer is currently too broken to boot into recovery mode."

Boot into a live environment - either the install disc or the Boot-Repair disc - back up your data and run your fscks, and then see where you are after that.

---

### Post by Gnusboy on 2019-07-12
Will do. Thanks

---

