---
title: "Says root partition full but it is definately not"
date: 2006-11-22
forum: General Help
---

### Post by odin1965 on 2006-11-22
Help my disk space has dissappeared. I have hda with four partitions. 
- hda1 is 40 NTFS with windows on it
- hda2 is 2gb swap
- hda3 is 22gb EXT3 with Edgy on it 
- hda4 is 47gb EXT3 with just some data on it. My home is on hda3 with edgy.
Last night I was trying to burn a CD and Serpentine came up with the error "not enough space in cache directory". Upon checking, I find the I have only 74mb free on my 22gb partition (hda3). When I open a window in Nautilus and right click and look at properties it says that the are so many item, totalling 2.7gb, not over 20gb. However it also says "some contents were unreadable". 

Has my partition somehow become corrupted? How can I get back my free space? I'm thinking it might be related to the trash somehow. I had a bunch of data on hda4 which is mounted on /mnt/Data which I recently went thru and cleaned out. I used the 'root nautilus here' script from Automatix and could delete stuff but kept getting the error 'cannot send items to trash, do you want to permanently delete them' or something similar. Could this stuff still be hidden somewhere and I can't see it because I'm not logged in as root?

---

### Post by aysiu on 2006-11-22
Can you post the output of this command? ```
df -h
```

---

### Post by odin1965 on 2006-11-22
Will try that when I get home from work. That is actually one of the list of things I was going to try just from gleaning as much info as possible from this forum. Will also try installing Boabob but there is probably not enough space. come to think of it, a few nights ago I left synaptic running while it was downloading quake2 over the dialup and it was closed in the morning. Bet I ran out of space while downloading a package.

---

### Post by ajgreeny on 2006-11-22
Also worth getting filelight and looking at exactly what is hogging all the space.  Filelight is a gui program which shows a very understandable pie chart of the partition or folder you chose, and how the files use the space available.  It should give you a graphical indication of where your space has gone.

---

### Post by odin1965 on 2006-11-22
Awesome, will try filelite too, if I can install it. May have to move the stuff frome my home directory temporarily to hda4

---

### Post by NoNo_231 on 2006-11-22
Since you use "root nautilus here" you have to go to the root home directory as root (This is the /root directory). Then Ctl+H or from nautilus Show hidden files. There is the trash (.Trash directory) of the root. Probably you could find many deleted items in the .Trash of the root. These are not shown at the trash icon of the Desktop, because the are different user's trash.

Hope it helps.

---

### Post by odin1965 on 2006-11-22
Here is the output fron df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              23G   22G   11M 100% /
varrun                221M  120K  221M   1% /var/run
varlock               221M     0  221M   0% /var/lock
procbususb             10M  124K  9.9M   2% /proc/bus/usb
udev                   10M  124K  9.9M   2% /dev
devshm                221M     0  221M   0% /dev/shm
lrm                   221M   18M  203M   9% /lib/modules/2.6.17-10-386/volatile
/dev/hda1              44G   41G  3.6G  92% /media/hda1
/dev/hda4              43G  6.2G   35G  16% /media/hda4
/dev/hdb1             276G  137G  125G  53% /mnt/Data

I tried going to the root directory and using 'root nautilus here' but there is no .trash file in the directory. Also looked at synaptic for filelight but it needs the KDE libraries which are 62mb and I don't have that much space.

Anybody got anymore ideas?

---

### Post by NoNo_231 on 2006-11-22
When you are in the root directory with the root nautilus do from the nautilus menu
View > Show Hidden Files
Then you will se a directory called .Trash.
See if it is empty or  how big it is.
Then you can go inside and delete these items, if you want.

---

### Post by odin1965 on 2006-11-22
Tried the 'root nautilus' show hidden files thing already. There is no .trash folder in root. This seems odd itself. I DID manage to install filelight as I already had the KDE dependencies installed. It shows my / file system to be only 2.9Gig about what it SHOULD be. Yet df -h show;

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              23G   22G     0 100% /

Really weird, eh? Now when I try to run the 'root nautilus here I get an error;
Failed to run /bin/echo 'got r00t?' as user root.
Unable to copy the user's Xauthorization file.

What would happen if I booted from the live CD, copied / and everything under it to a second drive, reformatted hda3, then copied everything back? Think it would work?

---

### Post by moshuptrail on 2006-11-22
You have 11M left on root.  Out of 33G.  Something is hogging space!
you can see the .Trash folder by going to root:
$ cd /
$ cd .Trash
$ ls -Slak
Will show all files sorted by size (largest first), with size in k

---

### Post by odin1965 on 2006-11-23
UPDATE:
I copied the contents of / to hda4 using "cp -R * destination". Even though there was only 2.9g visible, it copied the whole 22g that was filling up the hard-drive. The extra files seem to be in /var and I cannot delete them anyway I try.

I am giving up and reinstalling edgy. My install was only a week old, but I still had automatix and all my firefox extensions and various other things. I may copy them back from hda4 after reinstallation but then again I might just frag it just to be safe.

I have no idea what went wrong. I'll give edgy one more try and if it happens again it's back to dapper for me, at least on my main machine.

---

### Post by PapaNerd on 2007-03-08
This same pseudo-full “/” partition scenario bit me yesterday with a “df -h” showing 93% full on a 21GB partition, but summing the output from a “du” on each directory manually added up to only 3GB.  

After a lot of searching, I discovered that the /media directory showed filesystems on externally attached drives that had been unmounted and removed months ago.  In addition, the /media/cdrom0, /media/cdrom1, and /media/floppy0 directories listed several large (1+GB) files as present despite having no media whatsoever in the drives.  Once I removed these ghosts of the past, everything was fine again and the partition utilization report was back down to a more reasonable 13%.

Hope this info helps someone else!  I am curious if there is a bug report in the system for a fix since so many users are posting about this.

---

