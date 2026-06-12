---
title: "tar command to backup Ubuntu system ?"
date: 2013-09-08
forum: General Help
---

### Post by Coder88 on 2013-09-08
I have a really nice Ubuntu install tweaked, complete with all the software apps I need, Compiz effects, etc. I would like to back it up in case it succumbs to a case of fubar from either something i do or a system update/upgrade. I have used Clonezilla to do some partition cloning, but sometimes that does not work. I am getting better at learning Grub2 so I am feeling better about being able to restore Grub2 if needed, so I think a tar backup might suffice. Just that I want to be clear on a tar command to do what needs doing.

So say my Windows 7 system is on /dev/sda, my Ubuntu system ("/") is on /dev/sdb1, my /home is on /dev/sdb2, and I have an ntfs data drive with folders on /dev/sdc1  (that data drive is automagically mounted at boot by my Ubuntu system as /datadrive).

What tar command could I use to tar my Ubuntu system ("/") to /dev/sdc1 (without destroying that drive of course!), including the use of bzip? I want the highest compression, am willing to sacrifice execution time for highest compression. I have read it is important for such a tar to use excludes to exclude the .bzip tar file itself as well as various volatile system folders/files that do not need to be tarred because they are created during boot and only exist temporarily.

I came across this post on backing up an Ubuntu system using tar
[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)
but I want to understand it better and I want to be able to do such a tar backup where the tar archive is created and stored on /datadrive

From a terminal command line shell in my Ubuntu system, would this do what I need done? 
[FONT=courier new]$ sudo tar -cbvf /datadrive/backup.tar.bz2  /[/FONT]
My concern is that such a tar command would also try to include the  automagically mounted /windows and /datadrive folders, which of course  would be a disaster; so should i exclude them like this:
[FONT=courier new]$ sudo tar -cbvf /datadrive/backup.tar.bz2 --exclude=/datadrive --exclude=/windows   /[/FONT]

---

### Post by sudodus on 2013-09-08
If you move /home partition into the root partition, I have a system ready for you. Otherwise you can just make your own extra tarball of the home partition and store it separately.

Try the [One Button Installer, 'OBI']("http://ubuntuforums.org/showthread.php?t=2172971")

[FONT=sans-serif]It is very easy to make your own tarballs. But as before, it requires a simple configuration, only one [/FONT][FONT=sans-serif]partition for the system and one for swap.

[/FONT][FONT=sans-serif]There is also a possibility to install (as a second step) the OBI to an arbitrary sized drive and use all of [/FONT][FONT=sans-serif]it: For example a big USB pendrive (16GB or 32GB), or an external HDD or SSD (connected via USB [/FONT][FONT=sans-serif]or eSATA). This means that it can contain a rather big library of tarballs, or big tarballs, and can be [/FONT][FONT=sans-serif]used either to install from [/FONT][FONT=sans-serif]a large selection of tarballs, or to make and store [/FONT][FONT=sans-serif]backups[/FONT] [FONT=sans-serif]as tarballs.
[/FONT]

---

### Post by prodigy_ on 2013-09-08
[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

---

### Post by Coder88 on 2013-09-08
> **prodigy_ said:**
> [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

Um, yes, that link is in my original message/post. :)

---

### Post by Coder88 on 2013-09-08
Also, when I do
$ls /
I see home listed, even though home exists on its own drive partition. So when doing the tar command for a system backup, if I do NOT want home included in the backup, I would have to include the exclude for home in the tar command options, correct? so maybe:
[FONT=courier new]$ sudo tar -cbvf /datadrive/backup.tar.bz2 --exlude=/home --exclude=/datadrive --exclude=/windows   /[/FONT]

---

### Post by sudodus on 2013-09-08
I think this option will also prevent backing up other partitions, that are mounted.
     
```
--one-file-system
           stay in local file system when creating archive
```

But I suggest that you ***create a mini system to test your command lines*** before you go ahead with the real task. Then it will be easy to inspect the result either with ***file-roller*** or by extracting it to some other place.

---

### Post by Coder88 on 2013-09-08
Okay thank you. I am feeling close to pulling the trigger and giving a tar backup a go!

---

### Post by sudodus on 2013-09-08
Just a final thought. It is always easier to backup a system, that is not running. So if possible, boot from another system, mount the system you want to backup, and back it up. Otherwise things might change during the backup, so that it is not quite self-consistent (compatible with itself).

Otherwise you should exclude directories with files that are likely to change (and that might not be necessary in the backup).

---

### Post by Coder88 on 2013-09-08
> **sudodus said:**
> Just a final thought. It is always easier to backup a system, that is not running. So if possible, boot from another system, mount the system you want to backup, and back it up. Otherwise things might change during the backup, so that it is not quite self-consistent (compatible with itself).

Otherwise you should exclude directories with files that are likely to change (and that might not be necessary in the backup).

Excellent point. I am curious though, how much of a problem would it be to use a tarball created from a running linux system (very convenient of course, as one could stay productive), how reliable would such a tarball be for a restore? I don't know the answer to that question, just wondering.

I am running a tar backup now, scrolling by in a terminal. But once it completes I will do one from a live boot linux distro so my main linux system is not running during the tar backup. 

I was unable to run the tar using the bzip compression option, got an error about block sizes; so i am running a tar using gzip. I would like to figure out though how to do a higher compression. My goal is to get tarballs under 8GB (excluding /home) so they could easily be burned to a dual layer DVD for optical storage.

---

### Post by Coder88 on 2013-09-08
As my tarball is being created, to be stored on an ntfs data drive, I wonder if the resulting tarball filesize will be too large for ntfs? I guess I will find out. What is the maximum size of a tarball on linux? on windows/ntfs? Hmm. I guess if needed I could make a linux data drive for tarballs.

---

### Post by sudodus on 2013-09-08
> **Coder88 said:**
> Excellent point. I am curious though, how much of a problem would it be to use a tarball created from a running linux system (very convenient of course, as one could stay productive), how reliable would such a tarball be for a restore? I don't know the answer to that question, just wondering.

I am running a tar backup now, scrolling by in a terminal. But once it completes I will do one from a live boot linux distro so my main linux system is not running during the tar backup. 

I was unable to run the tar using the bzip compression option, got an error about block sizes; so i am running a tar using gzip. I would like to figure out though how to do a higher compression. My goal is to get tarballs under 8GB (excluding /home) so they could easily be burned to a dual layer DVD for optical storage.

I have no exact answer, but I recommend to backup from live boot so that your linux system is not running.

bzip2 is not included in tar, but you can pipe the output from tar to bzip2 and get the tarball you want.

```
sudo tar -cbv source | bzip2 > ball.tar.bz2
```

---

### Post by Coder88 on 2013-09-08
I made a tarball of my running ubuntu (ArtistX) system with this command:
```
sudo tar -czvf /Datadrive/ArtistX/artistx-system.gz --one-file-system  /
```
and it went well, resulting tarball was 5GB, small enough to easily burn to a dual layer DVD for optical storage backup.
Entire tar took 30 minutes.

I think I will try it again now with the piping ("|") to bzip2 to see if that will work, and to see the tarball filesize difference.

I love this aspect of linux-- an entire operating system and a gazillion apps, all able to be archived to a DVD optical disk! Mind you I am excluding /home but that is data, easy enough to backup separately and in more of a generic manner.

I just want to get smart on rescuing Grub2 for if and when that goes bad. But I can create some grub2 rescue instructions from reading posts here and on the web, be prepared, burn a SuperGrub2 dvd, etc.

---

### Post by Coder88 on 2013-09-08
> **sudodus said:**
> ... you can pipe the output from tar to bzip2 and get the tarball you want.

```
sudo tar -cbv source | bzip2 > ball.tar.bz2
```

1. So it is okay to leave off the f from -cbvf and just use -cbv  ?
2. Is the b needed in -cbv given it is being piped to bzip, could i just use -cv without the b ?
2. Can that command use the --one-file-system option?

So how would I modify my tar command to make use of bzip, e.g. what am i likely doing wrong with this command line?
[FONT=courier new]sudo tar -cv --one-file-system / | bzip2 > /Datadrive/artistx-system.bz2
EDIT: I am running the above command now, looks to be working.
(I actually have a folder /Datadrive/ArtistX/  as the target)

[/FONT]

---

### Post by sudodus on 2013-09-08
-f means to interact with the file specified after the -f. But if you pipe the output to bzip2, you should not send the output to a file directly. Let bzip2 redirect its output to the target file.

-b is not needed, but it may be efficient to copy block size chunks. The choice of options does not depend on your choice of output: to a file or piping to bzip2 (except -f of course).

-o-

NTFS and ex4 can manage huge files, hundreds of GB is no problem. But the file system of CD/DVD used to limit the file size to 2GB or 4GB. I'm not sure what file system you are using now. FAT32 limits the file size to 4GB. This is why Clonezilla strips the backup into 2GB files.

By the way, I think Clonezilla is as reliable as tar for complete backups. And the same basic rule holds for Clonezilla: boot from another drive to get a reliable backup. I use Clonezilla. But tar is good to make a system portable, because it can be installed/restored to a smaller partition.

Assuming you mount the partition to be backed up on /mnt

```
cd /mnt
sudo tar -cv --one-file-system . | bzip2 > /Datadrive/ArtistX/artistx-system.bz2
```

to get a relative address (the dot instead of the slash).

This is implemented in the One Button Installer (but I'm using gzip compression which is faster).

---

### Post by VMC on 2013-09-08
> **Coder88 said:**
> .... I have used Clonezilla to do some partition cloning, but sometimes that does not work....
I

I only use tar to backup my "/home" partitions, because I often re-install using the current iso. I use regex to only backup pertinent files/directories.:
```
tar cfpz /tmp/tarzan.tgz --exclude=home/user/.[^bv]* --exclude=home/user/Des* --exclude=home/user/Mus* --exclude=home/user/P[i,u]* --exclude=home/user/Tem* --exclude=home/user/Vid* ~user
```

I'm very curious about the above statement. Clonezilla has never failed to clone/restore any OS I've use. What problems to do you have with it?

---

### Post by Coder88 on 2013-09-08
> **VMC said:**
> ...Clonezilla has never failed to clone/restore any OS I've use. What problems to do you have with it?

I have used Clonezilla many times, regular image clones of my C: windows system. And did a few partition to image backups. But when I tried to do an image clone of an SSD drive, got fail error from zilla. Also was able to do partition to image backup of / of my ubuntu system, once, but then when i tried it again it failed. So I am going the tarball route for now. might get on Clonezilla forum and ask about this more.

---

### Post by Coder88 on 2013-09-08
> **sudodus said:**
> ...the file system of CD/DVD used to limit the file size to 2GB or 4GB. I'm not sure what file system you are using now. FAT32 limits the file size to 4GB. This is why Clonezilla strips the backup into 2GB files....

Another layer of tech to archive tarballs optically (DVD), hmm. Maybe something like peazip to take a large tarball and split it up into RAR files? I do have an external USB network drive I put data backups on, but I just think burning a tarball periodically to a DVD could be comforting, given the tarball size is under 8GB and that it could be burned to a DVD. Certainly can not archive my Windows 7 drive to a DVD!

---

### Post by sudodus on 2013-09-08
> **Coder88 said:**
> I have used Clonezilla many times, regular image clones of my C: windows system. And did a few partition to image backups. But when I tried to do an image clone of an SSD drive, got fail error from zilla. Also was able to do partition to image backup of / of my ubuntu system, once, but then when i tried it again it failed. So I am going the tarball route for now. might get on Clonezilla forum and ask about this more.

My experience is to repair the file system of the SSD before or during running Clonezilla.

Maybe the problem was that you tried to backup a running system with Clonezilla.

---

### Post by sudodus on 2013-09-08
> **Coder88 said:**
> Another layer of tech to archive tarballs optically (DVD), hmm. Maybe something like peazip to take a large tarball and split it up into RAR files? I do have an external USB network drive I put data backups on, but I just think burning a tarball periodically to a DVD could be comforting, given the tarball size is under 8GB and that it could be burned to a DVD. Certainly can not archive my Windows 7 drive to a DVD!

There are several drawbacks. Optical media are not really reliable. I suggest you use an external hard disk drive (eSATA or USB 3) instead of DVD disks. Or maybe two of them, to have two versions of backup, one of which in another house, if you want to be really sure to have a working backup also in case of fire or theft.

An alternative is to backup via the network (use for example rsync).

---

### Post by Coder88 on 2013-09-08
> **sudodus said:**
> ...Maybe the problem was that you tried to backup a running system with Clonezilla.

No, I was using Clonezilla Live CD (most current version as of yesterday). No other operating systems were operational.

---

### Post by sudodus on 2013-09-08
Well, some things remain hard to explain. But let us look forward: How are your tests with tar running?

Have you tried a mini-system to check, that the tarball can be restored to a 'perfect' copy of the original system?

---

### Post by erind on 2013-09-08
> **Coder88 said:**
> I have a really nice Ubuntu install tweaked, complete with all the software apps I need, Compiz effects, etc. I would like to back it up in case it succumbs to a case of fubar from either something i do or a system update/upgrade. I have used Clonezilla to do some partition cloning, but sometimes that does not work. I am getting better at learning Grub2 so I am feeling better about being able to restore Grub2 if needed, so I think a tar backup might suffice. Just that I want to be clear on a tar command to do what needs doing.

[...]


Another option to consider is **fsarchiver**, for full OS backups it's easier than *tar*.

[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

The feature that I like most is the restoration of a File System archive to a partition smaller than the original, and I used it just recently with a Ubuntu partition restore, from an old 80 GB disk to 25 GB new partition. It worked great.
Also  it supports different (nine) levels of compression, it can split the archive into smaller parts so they can be backed up say in DVD, etc ...

[http://www.fsarchiver.org/Compression#Compression_levels_available](http://www.fsarchiver.org/Compression#Compression_levels_available)

**fsarchiver **can be run from a different OS partition or a recent Ubuntu Live CD. The two most basic commands that you might need are:

```
# The paths below are just examples.
# Backup FS:

    fsarchiver savefs /data/backup/ubuntu_rootfs.fsa /dev/sda1


# Restore FS:

    fsarchiver restfs /data/backup/ubuntu_rootfs.fsa id=0,dest=/dev/sda1

```
More on its usage here:

[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

---

### Post by Coder88 on 2013-09-09
Nice, thank you. I am going to add fsarchiver to my arsenal and bag 'o linux tricks.

---

### Post by VMC on 2013-09-09
> **erind said:**
> Another option to consider is **fsarchiver**, for full OS backups it's easier than *tar*.

...In the past I had a lot of issues with fsarchiver , CRC failed, and then trying to restore failed as well. It has been well over 1 1/2 years since I last tried it, so you have pique my interest, since there has been a lot of changes since then. Here are my results with both partclone and fsarchiver:```
$ date;sudo ./fsarchiver -j2 savefs /media/user/ext4/Ubuntu.fsa /dev/sda7;date
...07:59:19...
Statistics for filesystem 0
* files successfully processed:....regfiles=110585, directories=18276, symlinks=46127, hardlinks=0, specials=84
* files with errors:...............regfiles=0, directories=0, symlinks=0, hardlinks=0, specials=0
...08:03:59... 
total =>** 4min41sec**
====
$ date;sudo ./partclone.ext4 -N -c -s /dev/sda7 -o /media/user/ext4/ubuntu;date;sudo gzip --fast /media/user/ext4/ubuntu;date
...10:11:55...
Cloned successfully.
...10:14:01... => 2min6sec
...10:15:49... => 1min48sec (gzipping)
total => **3min54sec**
```
This is a drastic improvement over the older version. It took over 11min to backup my ubuntu partition.
Even though partclone is faster, fsarchiver compressed the output more, so that eats up some time.
The newest partclone has a new *curses* feature on both clone and restore which gives a more polished look. It use to be only on restore.

I'm unsure if the multi-core feature was available on the older fsarchiver that I used, but adding "-j2" for my dual-core really speed up the process.

---

### Post by erind on 2013-09-09
> **VMC said:**
> [...]

This is a drastic improvement over the older version. It took over 11min to backup my ubuntu partition.
Even though partclone is faster, fsarchiver compressed the output more, so that eats up some time.
[...]

It's been pretty efficient for me as well - a fsarchiver backup/restore of about 20GB FS took about 15-20 min, final archive size was about 11GB (all default settings). I haven't used the fsarchiver's older versions or partclone, so can't comment on that.
In my recent backup/restore the original old disk was 80GB, total FS size was ~20GB, the final archive was 11GB, and it was restored to a new smaller partition of 25GB. 
No issues either with Ubuntu or a Windows operation, (always used on unmounted OS partitions). I've had to simply run Boot-Repair for a final boot restore and that was it. 
What really drew me into fsarchiver, was its ability to backup a FS into a smaller partition than the original one. All in all a very useful backup utility.

---

