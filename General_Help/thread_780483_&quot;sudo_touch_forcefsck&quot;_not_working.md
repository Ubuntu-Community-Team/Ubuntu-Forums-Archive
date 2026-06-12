---
title: "&quot;sudo touch forcefsck&quot; not working"
date: 2008-05-03
forum: General Help
---

### Post by gsub on 2008-05-03
hi, all.

like the subject title says, once i issue the commands

cd /
sudo touch forcefsck

and then reboot, the system starts up as usual, and the file i just created is removed.

anyone know how to force fsck on boot in Hardy?

Cheers.

---

### Post by mike2357 on 2008-05-03
Gee, it looks like you have it right.  Two suggestions:

1.  After you do the touch command, do an "ls -l /forcefsck" to make sure it worked OK.
2.  Take a look at /var/log/fsck/checkfs.  It's the output log file and maybe it will provide a clue.

I had a similar problem several months ago.  It turned out that I had a typo in "forcefsck".  Duh.

---

### Post by gsub on 2008-05-03
Believe it or not, those are the first things i tried before heading over to the fora to cry for help.

The file is indeed there in the directory (albeit occupying zero bytes).

the /var/log/fsck/checkfs file contains a log of all the fsck's carried out at boot - just one since i upgraded to hardy (reproduced below)




Log of fsck -C3 -R -A -a 
Sat May  3 12:12:00 2008

fsck 1.40.8 (13-Mar-2008)

Sat May  3 12:12:00 2008
----------------

---

### Post by mike2357 on 2008-05-03
I gave it a whirl myself, and it worked fine.

**Results from /var/log/fsck are:**

Log of fsck -C3 -R -A -a -f
Sat May  3 17:44:23 2008

fsck 1.40.8 (13-Mar-2008)

Sat May  3 17:44:23 2008
----------------

**Results from /var/log/checkroot are:**

Log of fsck -C4 -f -a -t ext3 /dev/sda2
Sat May  3 17:42:03 2008

fsck 1.40.8 (13-Mar-2008)
/dev/sda2: 149881/13549568 files (2.1% non-contiguous), 2765417/27091614 blocks

Sat May  3 17:44:21 2008
----------------

Sorry I can't be of more help.  Maybe something above will give you a clue.

---

### Post by gsub on 2008-05-04
It's the strangest thing... Hardy had a bunch of updates to install this morning (1 pm). After installing them, i tried the touch /forcefsck, and it worked.

and it has a new look, and a bypass feature - i dont have to bother doing sudo touch /fastboot anymore. (or did it always have it? <duh> )

---

