---
title: "fsck died with exit status 4, Help me"
date: 2007-05-19
forum: General Help
---

### Post by Nehvrook on 2007-05-19
I have been playing around with Ubuntu for a while now. I recently installed 7.04 and today it started up and said the drive has been mounted 30 times and a check will be forced. I've searched the forums and found this is normal. However after getting so far through this forced check it spews out a load of messages I don't understand and ends up saying "fsck has died with exit status 4"
This has happened once before (Though I'm not sure it was exit status 4 before). Last time I assumed there was a random corruption in my hard drive so I formated and re-installed. I'm just wondering if there is a way to fix this problem or something I should know to avoid it next time? Or is my hard drive just bust and should I get a new one?
I've searched the forums and google and I can't find anything about what this means or how to fix it. Can anyone help me?

---

### Post by Nehvrook on 2007-05-19
Just some additional information that might be useful to anyone helping me (I was in a rush posting the last post :P)

I'm dual booting Windows XP and Ubuntu 7.04. Both are on seperate SATA hard drives.

I'm not sure if it's relevant but I recently installed on Windows a driver to let me view the hard drive with Linux on it (It didn't recognise the file type). However since installing this driver I booted up several times with no problem. (Maybe it's just since it's checked this time?)

I'm really quite new to Linux so I'm not even sure where to start. In threads that I've read that seem related (Though I can find none on the same problem exactly) people are talking about using fsck to manually fix the problem. But I wouldn't know how to do this.

Again, any help will be apreaciated. Thanks

---

### Post by Nehvrook on 2007-05-19
Bump

---

### Post by Nehvrook on 2007-05-20
Okay, sorry about this but one more bump. If nobody replies this time I'll assume nobody knows an answer and I'll go get a new Hard Drive.

---

### Post by hexion on 2007-05-20
I wouldn't rely on fsck to decide wheter your disc went bust or not..
Better take a look for disc utilities like seagate's one. Go to your HDD brand's web to find them, and if you can't (or they don't have utilities) use generic ones.

A deep test to your drive will surely help you to know if it's a hardware problem or not. Note, the problem can be in your HDD, in your motherboard, or even in your power supply, so if the test fails you need to consider all those options.

If you pass the test without errors, continue using your system. A fsck error like that could be just caused by a random electric problem or so...

Hope it helps. Anyway, if nobody with more knowledge than me replies you, don't give up (there are lots of threads here and surely they haven't read it). For urgent problems, IRC channels are the best option.

---

### Post by hexion on 2007-05-20
Mmmm... reading your 2nd post I'm quite sure it's not a hardware problem.

If your system works well don't worry..

BTW, to manually fix your partition:
- Boot a live-cd
- Open a terminal
- Find the dev associated to the partition you want to check with:
> sudo fdisk -l
- fsck it (i.e. assuming it's /dev/sda1)
> sudo fsck /dev/sda1

Good luck.

---

### Post by Nehvrook on 2007-05-20
Hi, thanks for the reply. I was saying because my other hard drive (with windows) works fine I can assume my motherboard and power supply are still okay. And this hard drive has always been a bit iffy (I got a lot of randomly corupted data when I used it for storing files in the past).

I ran fsck in the terminal on the live CD like you suggested. I got this 

/dev/sda1: recovering journal
/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error reading block 15302758 (Attempt to read block from filesystem resulted in short read) while doing inode scan.  Ignore error<y>?yes

Force rewrite<y>? no

Error reading block 15302759 (Attempt to read block from filesystem resulted in short read) while doing inode scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 15302760 (Attempt to read block from filesystem resulted in short read) while doing inode scan.  Ignore error<y>? yes

And then it's stuck like this asking the same question but putting the block number up by one each time.

Does this help identify the problem?

---

### Post by hexion on 2007-05-20
Why did you answer yes to the "ignore error" question? We want fsck to repair the problem, not to ignore it ;)

Well, if that HDD has given you errors in the past and considering the blocks with error are consecutives... I think it would be a good idea to buy a new one (if you can afford it it's the easiest and safest solution)

Or at least not to use that disk for the system partition... using it to store movies or not-so-important data would be an option.

Anyway, if you don't consider trashing your HDD, I would suggest you to use a hard disk utility to mark the bad sectors as non-usable and then store unimportant data on it.

HDDs fail much more we would like them to... at least if you can recover your most important data you can feel lucky....

Good luck.

---

### Post by Nehvrook on 2007-05-21
Hi. Sorry, the reason I said ignore was I didn't realise there was another choice, stupid mistake I know lol. I just assumed that if I chose not to ignore it it wouldn't continue.
Anyway I did it again and chose not to ignore and I got this:

ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error reading block 15302758 (Attempt to read block from filesystem resulted in short read) while doing inode scan.  Ignore error<y>? no

Error while scanning inodes (7654144): Can't read next inode
e2fsck: aborted


Which isn't to helpful.

But anyway I'm just letting you know what's happening, I've bought a new hard drive and I'm just gonna install Ubuntu on that one. I haven't lost any files (I've got two hard drives and an external, and my windows partition can still read my linux drive so anything that wasn't backed up is rescuable. So no worries)

Thanks for your replies :)

---

### Post by nismoskys on 2007-05-29
i've just installed fiesty, never even got to boot up the system because i keep getting the same error as nehvrook got. 

i booted up the live, ran fsck, and this is what i get.```
ubuntu@ubuntu:~$ sudo fsck /dev/hdb2
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/hdb2: recovering journal
/dev/hdb2: clean, 98408/2260992 files, 592221/4516273 blocks
ubuntu@ubuntu:~$ 

``` yet i still get a hang on boot up, followed by a disk check, followed by fsck status 4 error.

anyone know what's going on?
thanks.

---

### Post by Arizon_Dread on 2007-10-08
I have the same error.

I tried to copy a directory onto a USB memory. after it was finnished, the usb memory couldn't be stopped. so I waited and waited. and after while I just yanked it out. then I put it back in, and it was read only.

so. I copied all the folders to desktop EXCEPT the one I tried to copy to the usb memory in the first place. then i ejected and pulled it out. rebooted into XP and browsed the memory. I could read all the files except that corrupted folder, so I copied the other folders to the desktop in winxp, and formatted the usb memory. then I rebooted into ubuntu and got this problem that has been posted about earlier.

here's the log:

```
Log of fsck -C -R -A -a 
Mon Oct  8 21:10:18 2007

fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda8: 0 files, 1/1739112 clusters
/dev/sda7: clean, 38/48192 files, 45397/192748 blocks (check after next mount)
/dev/sda6 contains a file system with errors, check forced.
Error reading block 18655105 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 9322610.  

/dev/sda6: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
/dev/sda9: clean, 9207/6881280 files, 2189454/13741591 blocks
fsck died with exit status 4

Mon Oct  8 21:11:08 2007
----------------

```

when I got to the login screen, my home dir didn't excist. so I booted with the live CD and found that it had been moved. so I copied it to the right place (ofcourse I wasn't smart enough at the moment to move everything EXCEPT usb memory backup folder (which I found out to be corrupted after I moved the stuff). Now I can boot ubuntu, but I get this hangup every time at bootup. 

I have removed the folder with shift + delete now, but I still get the hang up. how can I make the part of the harddrive non-usable so the OS works around those corrupted parts? will it help if I format? 

the hard drive is no more than a few months old and I think it's due to this corrupted folder that it's malfunctioning.

PLEASE come with a suggestion?:(

---

### Post by adn258 on 2008-02-13
> **Arizon_Dread said:**
> I have the same error.

I tried to copy a directory onto a USB memory. after it was finnished, the usb memory couldn't be stopped. so I waited and waited. and after while I just yanked it out. then I put it back in, and it was read only.

so. I copied all the folders to desktop EXCEPT the one I tried to copy to the usb memory in the first place. then i ejected and pulled it out. rebooted into XP and browsed the memory. I could read all the files except that corrupted folder, so I copied the other folders to the desktop in winxp, and formatted the usb memory. then I rebooted into ubuntu and got this problem that has been posted about earlier.

here's the log:

```
Log of fsck -C -R -A -a 
Mon Oct  8 21:10:18 2007

fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda8: 0 files, 1/1739112 clusters
/dev/sda7: clean, 38/48192 files, 45397/192748 blocks (check after next mount)
/dev/sda6 contains a file system with errors, check forced.
Error reading block 18655105 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 9322610.  

/dev/sda6: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
/dev/sda9: clean, 9207/6881280 files, 2189454/13741591 blocks
fsck died with exit status 4

Mon Oct  8 21:11:08 2007
----------------

```

when I got to the login screen, my home dir didn't excist. so I booted with the live CD and found that it had been moved. so I copied it to the right place (ofcourse I wasn't smart enough at the moment to move everything EXCEPT usb memory backup folder (which I found out to be corrupted after I moved the stuff). Now I can boot ubuntu, but I get this hangup every time at bootup. 

I have removed the folder with shift + delete now, but I still get the hang up. how can I make the part of the harddrive non-usable so the OS works around those corrupted parts? will it help if I format? 

the hard drive is no more than a few months old and I think it's due to this corrupted folder that it's malfunctioning.

PLEASE come with a suggestion?:(

Yeah I have been having the same problem and a lot of my files were deleted after this.  I just backed up the thing I think we shouldn't let fsck check your system.

---

