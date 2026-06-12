---
title: "Hard Drive question after deleting file.. size doesent change back"
date: 2006-11-30
forum: General Help
---

### Post by mathersalan on 2006-11-30
Hello all,


I downloaded a game called Quake 4 which had to be done through the root in order for it to run.

Well I had problems that required me to delete the 2.9gb quake folder from my root (usr/local/games/quake4) and when I did I found that the HDD size did not change like it was suppose to when you delete something at that size.. 

For example.

I have a 20 gb HDD... Before I installed the big 2.9gb files into the root I had a good 12 GB s of free space.. it came down to 9 GB s after installing the Quake 4 files..went to delete it..right clicked sent to trash empty trash and the hdd still had 10 gb of space left..then restarted still no change and I did all this from the root.. 

I deleted it because I screwed up on the files and wanted to start over.. so I installed 2.9gbs back into the root..the hard drive size amount went to 6 gb's... everything works for the game now but the question is why is it doing this?  If I deleted it.. it should be deleted for good...

---

### Post by mathersalan on 2006-11-30
I tried fdisk this comes up

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2330    18715693+  83  Linux
/dev/hda2            2331        2434      835380    5  Extended
/dev/hda5            2331        2434      835348+  82  Linux swap / Solaris



now I have 2.6 gbs of HDD space gah 


mathersalan@mathersalan:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              18G   15G  2.6G  85% /
varrun                379M   84K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
procbususb             10M  128K  9.9M   2% /proc/bus/usb
udev                   10M  128K  9.9M   2% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   18M  362M   5% /lib/modules/2.6.17-10-generic/volatile

---

### Post by igknighted on 2006-11-30
if you deleted it through the GUI it might have just gone to the trash.  If it is in the trash you need to empty the trash to clear the hard drive space.

---

### Post by mathersalan on 2006-11-30
When I sent to trash I emptied it.. 

Maybe it's there but I cannot see it? I tried the view hidden folders did not see anything in it


I checked the disk analyzer ad it said Total filesystem capacity: 17.6 gb (used: 14.1 GB available: 3.5 gb)


i scannred it and the directory / has 8.9 gb s (red)

---

### Post by CatKiller on 2006-11-30
If you deleted them as root through the GUI, they'll be in root's wastebasket. The files are probably in /root/.Trash.

---

### Post by mathersalan on 2006-11-30
omg thank you a lot.. I looked through the / directory through sudo nautilus
and couldent find the .Trash but I forgot about the hidden files/folders lol 


now I leared something today.. kinda 8)

---

### Post by dubrict on 2006-12-05
Hello, what if I have this same problem and that's not the solution?  I deleted 4gb's worth of Half-Life and it never cleared up.  I used the rm -r command from the terminal, not as the sudo user.  The trash is empty...

---

