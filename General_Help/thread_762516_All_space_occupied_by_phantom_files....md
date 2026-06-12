---
title: "All space occupied by phantom files..."
date: 2008-04-22
forum: General Help
---

### Post by POW R TOC H on 2008-04-22
Hello. I have a problem I need to solve as soon as possible, in order to be able to continue to function normally... Unfortunately, I can't solve it myself :(

I have installed virtualbox from synaptic, because I needed to install windows in order to use some programs wine couldn't emulate (probably because it's not an emulator :) , but you know what I mean). However, this caused the partition on which / (root) sits to be completely filled... My /home folder is mounted to another partition, and has about 150Gb, but / has about 8Gb. Anyway, I have removed virtualbox via apt-get remove, but the space isn't freed. I suppose the space is ocupied by the virtual hard drive created by virtualbox, but I have no idea where it is...

Can you help me delete this bloated file, to restore function of my Ubuntu :) ?

---

### Post by ibuclaw on 2008-04-22
Open up synpatic, and choose your filter as "Status", then select (If there) the "Not Installed (Residual)" Option, select all packages within the list and mark them to "Completely Remove".

Or to get the same list in the terminal, type in:
```
dpkg -l | awk '{if ($1=="rc") print $2 }'
```
And you can purge those packages.
```
sudo aptitude purge **package1 package2 etc...**
```

If the problem is with VirtualBox, you can locate them.
ie:
```

sudo updatedb
locate vbox
locate virtualbox
locate .VirtualBox

```
And remove them as they aren't needed anymore.


You can also track down the source of the bloat using **du**

ie: something like:
```
du -h --max-depth=1 --exclude='/home' --exclude='/media' / 2>/dev/null

```
Where:
-h = human readable file/folder size (45.7M = 45.7MB)
--max-depth=1 = only output the folder sizes in the directory given.
--exclude='' = exclude your /home and /media partitions as they are not part of the root filesystem.
/ = the folder you are scanning
2>/dev/null = blank out any errors, ie: "cannot read directory: Permission Denied"

You'll have an output like this:
```

4.0K	/initrd
173M	/lib
16K	/lost+found
96K	/dev
5.3M	/bin
32K	/tmp
5.8G	/usr
6.7M	/sbin
19M	/boot
33M	/etc
1.2G	/opt
0	/proc
4.0K	/srv
4.0K	/mnt
378M	/var
69M	/root
0	/sys
7.6G	/

```
So now you can track down any uncommonly large areas.
ie: I have a 1.2GBs of data in my /opt folder, but I've never used it before...
So that is something worth investigating!

Happy Hunting!

Regards
Iain

---

### Post by odinfromvalhalla on 2008-04-22
Open VirtualBox and go to File -> Preferences. 

There in the General tab you should have the Default Folders settings.

---

### Post by POW R TOC H on 2008-04-22
Thanks guys!

---

### Post by buntu_hugenewbie11 on 2008-05-13
So I seem to have a similar problem where all of a sudden I have no HD space, my question is should I be worried about the 18gigs in / ?
I just am out of space and I do not know how to go about getting more space?

48K     /lost+found
346M    /var
14M     /etc
5.7M    /bin
66M     /boot
136K    /dev
9.5G    /home
4.0K    /initrd
525M    /lib
8.0K    /mnt
4.0K    /opt
0       /proc
14M     /root
6.5M    /sbin
4.0K    /srv
0       /sys
3.3M    /tmp
7.4G    /usr
4.0K    /name1
3.1M    /lib32
18G     /

---

### Post by zvacet on 2008-05-13
@ **buntu_hugenewbie11**

You used 18 GB in root?Of course it is too much but I don´t know what are you doing ( installing).Are you runing server or do you have VM installed? You can make some space with 

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```

---

### Post by buntu_hugenewbie11 on 2008-05-13
No I am not running a server or anything like that.
This is just a laptop that I use mostly for work. I do have some extra software like Stata.
How can I find what I have as root?
It just seems like this is too much space for what I do.
What is the best way to find which packages I have?

---

### Post by buntu_hugenewbie11 on 2008-05-13
After a restart the / directory dropped to 8 gigs.
Why would this be happening?

---

