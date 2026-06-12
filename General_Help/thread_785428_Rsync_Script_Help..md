---
title: "Rsync Script Help."
date: 2008-05-07
forum: General Help
---

### Post by Roasted on 2008-05-07
Okay, minor issue. I just upgraded to Hardy and I was trying to set up my backup script.

I have 3 hard drives in my computer. 
Drive "A" is for XP/Hardy. 
Drive "B" is for backing up my home directory on Drive "A", and it also has shared folders for my mom and two brothers, so they can back stuff up to "Drive B" over the network (samba).
Drive "C" simply copies Drive "B" 100% via the script.

SDC2 = Drive B
SDA1 = Drive C

My script.

#!/bin/bash
sudo mount /dev/sdc2 /media/driveb
sudo mount /dev/sda1 /media/drivec
sudo rsync -a --progress --delete ~/ /media/driveb/jason
sudo rsync -a --progress --delete /media/driveb /media/drivec

So I'm copying my home dir on Drive A to MY folder on Drive B (because there are folders on Drive B for my brothers and mom, so I needed to specify it go to my particular folder). Then, I copy the entire contents of Drive B to Drive C. Make sense?

Well, I ran into some errors. So I ran the rsync command individually from the script. I ran the first one out of the two, where I rsync my home directory from Drive A to Drive B. (~/ /media/driveb/jason)

And I get this:

jason@jason-desktop:~$ sudo rsync -a --progress --delete ~/ /media/driveb/jason
building file list ... 
rsync: readlink "/home/jason/.gvfs" failed: Permission denied (13)
39589 files to consider
IO error encountered -- skipping file deletion
.bash_history
        8775 100%    0.00kB/s    0:00:00 (xfer#1, to-check=39585/39589)
.xsession-errors
       75895 100%   72.38MB/s    0:00:00 (xfer#2, to-check=39568/39589)
.gconf/apps/nautilus/preferences/
.gconf/apps/nautilus/preferences/%gconf.xml
         432 100%  421.88kB/s    0:00:00 (xfer#3, to-check=39234/39589)
.gconfd/
.gconfd/saved_state
       96318 100%   30.62MB/s    0:00:00 (xfer#4, to-check=39092/39589)
.mozilla/firefox/as8cvuu7.default/
.mozilla/firefox/as8cvuu7.default/cookies.sqlite
      164864 100%   31.45MB/s    0:00:00 (xfer#5, to-check=34684/39589)
.mozilla/firefox/as8cvuu7.default/Cache/_CACHE_001_
      790880 100%   41.90MB/s    0:00:00 (xfer#6, to-check=34491/39589)
.purple/
.purple/blist.xml
       33794 100%    1.70MB/s    0:00:00 (xfer#7, to-check=34171/39589)

sent 2546059 bytes  received 198 bytes  5092514.00 bytes/sec
total size is 115299748731  speedup is 45282.05
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]
jason@jason-desktop:~$


What I did was, I created the directories (Drive B and Drive C) in /media, and granted 777 rights to each folder.

Then I went to /usr/local/bin where my backup script is stored and granted 777 rights to it, as well as chmod +x to execute it.

I honestly don't think I did anything differently this time around than I did the last few times with the previous versions of Ubuntu. The one thing I did notice is when I installed Hardy, it changed my drive identification. Previously, SDB2 was the ext3 partition on Drive B. But now, it's my swap space on Drive A. Kind of weird, but I changed all of the ID's accordingly so the script should still see what it needs to see and do what it's instructed to do.

Can anybody help?

---

### Post by grim4593 on 2008-05-08
Well, i ran into one of your problems as well:
```
rsync: readlink "/home/<username>/.gvfs" failed: Permission denied (13)
<number> files to consider
IO error encountered -- skipping file deletion
```
It caused the old files not to get deleted on the drive, and the space filled up quick.
What i did to get around it was to add "/home/<username>/.gvfs" to an exclude file, inserting in your username, and then when you run the command add "--exclude-from=<file>". If you don't want to have an exclude file, you can just do "--exclude=/home/<username>/.gvfs" to the command line argument to do the same thing.

You can check out the exclude options by using "man rsync".

---

### Post by vanadium on 2008-05-08
Also mount your partitions using UUID or LABEL to avoid problems with changing device names.

---

### Post by Roasted on 2008-05-11
What is this gvfs? It's in my home directory... perhaps it's a bad setting in my home directory? I didn't format my home directory when I upgraded. Do you guys think that could be the problem? Should I format my home directory and pull the info back over and see what happens?

---

### Post by Roasted on 2008-05-12
Although I expected something to happen, I just wanted to confirm this... If you are like me and you keep your root and home on separate partitions, don't ever boot to the livecd and format only the home partition. When you reboot, things just don't work right.

Currently reinstalling Hardy with a fresh home partition. Ever since I upgraded to Hardy by doing a fresh install (yet not formatting my home partition from gutsy) I've had weird issues that enrage me. Maybe this will help. 

I'll edit this tomorrow when it's done installing.

---

