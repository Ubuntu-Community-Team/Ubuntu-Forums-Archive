---
title: "BackUp image of HD on external HD"
date: 2007-08-27
forum: General Help
---

### Post by abhiroopb on 2007-08-27
I am currently running Ubuntu feisty 7.04.

I have a 100gb HD which has about 37gb of data on it.

I have an external (USB) HD which is 60gb.

Basically I have a simple request: I have got my ubuntu installation JUST the way I want it, so now I want to make one backUp of this onto my external HD. After which I want to have enough space left over to periodically backup my home folder (which is about 27gb).

I know this seems like an odd request becuase I'm backing up the same thing twice but what I want is to be able to restore a file/folder, if I have made some stupid error, quickly and efficiently without relying on any (potentially) bugg software. So a simple copy and paste of my home folder is all I need.

On the other hand I would also like to make an entire image of the hard drive so that if there is any major problem I can use it to restore everything just the way I want it.

This image I will only do once or at most if I make any major changes I'll do it again, basically its a failsafe. But it would need to be zipped so I can accomodate my home folder as well.

I have been browsing through many threads and none of them really seem to provide a good ste-by-step detailed explanation of what I need.

I don't mind taking the effort to back it up once as I can read the thread, but my main worry is lets say I crash my ubuntu installation then I need a quick way retore the partition (even if I can't rely on any online threads).

Finally I am not very fluent with the command line and I'd rather not have to improvise anything as I know how dangerous all the editing can be.

So to give final details: 
1. 100gb HD (37.7gb used)
2. 60GB external HD 

3. Backup image of 37.7gb (possibly zipped) to 60gb HD
4. Backup home folder periodically (every night/week) to 60gb HD

5. Quick painless restore if things go to hell

Any suggestions?

---

### Post by eddietours on 2007-08-27
:guitar: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by abhiroopb on 2007-08-27
Thanks for that.

I actually downloaded the cd and burnt an iso of it. But what I really need help with is how to mount the external hard drive and what I need to type in at the terminal the help isn't very clear.

---

### Post by rsambuca on 2007-08-28
The system rescue disc can come in handy, but for your purposes, you really only need the Partimage program.  It is in the standard ubuntu respositories, so you can just install it using the Synaptic Package manager, or using the command line with ```
sudo apt-get install partimage
sudo apt-get install partimage-doc 
```

The website is located [[COLOR="Red"]here[/COLOR]]("http://www.partimage.org/Main_Page")

---

### Post by wirelessmonkey on 2007-08-28
However, to make an image of your drive, you'll need partimage on CD anyway, so you might just as well use the sysresccd.


After it boots, you 'll need to determine the name of each of our devices, probably /dev/sda and /dev/sdb

so, assuming this is correct, and your backup drive is formatted already...
mkdir /mnt/backup
mount /dev/sdb(the drive your are backing up to) /mnt/backup

just run 'partimage' from the commancd line, and you'll get a curses interface.
Choose the options you want, and for path name use /mnt/backup/nameofyourbackup

Ta-Da!

---

### Post by abhiroopb on 2007-08-28
> **wirelessmonkey said:**
> However, to make an image of your drive, you'll need partimage on CD anyway, so you might just as well use the sysresccd.


After it boots, you 'll need to determine the name of each of our devices, probably /dev/sda and /dev/sdb

so, assuming this is correct, and your backup drive is formatted already...
mkdir /mnt/backup
mount /dev/sdb(the drive your are backing up to) /mnt/backup

just run 'partimage' from the commancd line, and you'll get a curses interface.
Choose the options you want, and for path name use /mnt/backup/nameofyourbackup

Ta-Da!
Thanks a lot. Worked like a charm! I used sys rescue cd and it said not to use /mnt cos it would crash. So I just used /backup.

---

