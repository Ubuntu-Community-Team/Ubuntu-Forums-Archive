---
title: "Home folder &quot;full&quot;?"
date: 2008-05-17
forum: General Help
---

### Post by lackofcreativity on 2008-05-17
Very odd problem. For some reason, I can't save anything to my home folder. The exact message it returns varies depending on the program, but this is what winecfg showed me when I tried to change some of Wine's settings...
```
 wineserver: could not save registry branch to user.reg : No space left on device 
```
I have confirmed that there are 8.6 GB free on my disk. This, tragically, makes it so I can't save any changes to my settings files; Nexuiz requires reconfiguring every time it starts, Firefox can't save history or bookmarks, and I can't save anything to Wine's virtual C:\ drive without using sudo. sudo is the only way I can save things to my own home folder, and using chmod on my home folder with the -R option doesn't seem to help. I thought about running everything as root, but that poses a huge security risk. Please, help me!

---

### Post by ibuclaw on 2008-05-17
Open up a terminal type in:
```

cd /home
ls -l

```
Take note of whether or not "**yourname**" appears three times in the line.
If your home folder doesn't say something like this:
```
drwxr-x--- 89 yourname   yourname   4096 2008-05-17 22:35 yourname
```

Just for good measure, type in the following commands:
```

cd /home
sudo chown yourname yourname -R
sudo chgrp yourname yourname -R

```
Replace "yourname" with your username, of course!

Regards
Iain

---

### Post by Gunman1982 on 2008-05-17
Please execute the command 'df -h' in the console and show the output.

---

### Post by ibuclaw on 2008-05-17
> **Gunman1982 said:**
> Please execute the command 'df -h' in the console and show the output.

Those were exactly my first thoughts, but I figured that must not be the issue as the OP has said that he can create files with "sudo". And forgive me if I'm wrong, but sudo still uses your home directory, not the "/root" folder to store all it's settings.

But now that you've meantioned it, I suppose I can't dismiss the fact that all clues are welcome! :)

Regards
Iain

---

### Post by Gunman1982 on 2008-05-17
> **tinivole said:**
> Those were exactly my first thoughts, but I figured that must not be the issue as the OP has said that he can create files with "sudo". And forgive me if I'm wrong, but sudo still uses your home directory, not the "/root" folder to store all it's settings.

But now that you've meantioned it, I suppose I can't dismiss the fact that all clues are welcome! :)

Regards
Iain
Oh sorry overread that bit *cough* *whistle*

Than the solution of tinivole should be the right one. If you just want to execute one line you can do
'sudo chown -R username.username /home/username'

---

### Post by lackofcreativity on 2008-05-19
Uhhh....
```
shawn@ubuntu:/home$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             9.3G  9.0G     0 100% /
varrun               1007M  104K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M   56K 1007M   1% /dev
devshm               1007M   12K 1007M   1% /dev/shm
lrm                  1007M   43M  965M   5% /lib/modules/2.6.24-16-generic/volatile
/dev/sdb3              17G  8.2G  8.6G  49% /media/hda3
overflow              1.0M   68K  956K   7% /tmp
gvfs-fuse-daemon      9.3G  9.0G     0 100% /home/shawn/.gvfs
/dev/scd0             700M  700M     0 100% /media/cdrom0

```
And...
```
shawn@ubuntu:/home$ sudo chgrp shawn shawn -R
chgrp: cannot access `shawn/.gvfs': Permission denied

```
And...
```
shawn@ubuntu:/home$ ls -l
total 8
drwxr-xr-x  2 root  root  4096 2008-04-26 19:09 java
drwxrwxrwx 62 shawn shawn 4096 2008-05-19 15:40 shawn

```
And finally...
```
shawn@ubuntu:/home$ sudo chown shawn shawn -R
[sudo] password for shawn: 
chown: cannot access `shawn/.gvfs': Permission denied

```
Now when I log in it says something about a folder in my home (can't remember exactly what it was, but it was . something...) not being writable (I think...).
Getting rid of the "sudo" yields...
```
shawn@ubuntu:/home$ chown shawn shawn -R
chown: changing ownership of `shawn/.gvfs': Function not implemented
shawn@ubuntu:/home$ chgrp shawn shawn -R
chgrp: changing group of `shawn/.gvfs': Function not implemented

```
Thanks for the help, though!

---

### Post by lackofcreativity on 2008-05-19
Wait a sec...
It was my other hard drive partition that was about half full. The filesystem says it has 0 bytes free, and it says its total size is 9.3 GB but only 9.0 is in use. Going to try some resizing to see if it helps...

---

### Post by mannheim on 2008-05-19
> **lackofcreativity said:**
> Uhhh....
```
shawn@ubuntu:/home$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             9.3G  9.0G     0 100% /
varrun               1007M  104K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M   56K 1007M   1% /dev
devshm               1007M   12K 1007M   1% /dev/shm
lrm                  1007M   43M  965M   5% /lib/modules/2.6.24-16-generic/volatile
/dev/sdb3              17G  8.2G  8.6G  49% /media/hda3
overflow              1.0M   68K  956K   7% /tmp
gvfs-fuse-daemon      9.3G  9.0G     0 100% /home/shawn/.gvfs
/dev/scd0             700M  700M     0 100% /media/cdrom0

```


The first line says that your filesystem on /dev/sdb1 (which includes your home directory, apparently) is completely full. The reason that you can save some stuff when using sudo is that (I think) a linux filesystem such as ext3 will reserve some blocks to be used only by root, not by regular users. The purpose of these reserved blocks (I guess) is to allow some wiggle-room when things get bad.

---

### Post by lackofcreativity on 2008-05-19
Makes total sense. Adding a couple gigs to it at the moment, and trying to figure out how I filled up all 9 gigs in just a month!
EDIT: Oh wait, no Applications menu; just makes a 2 by 2 pixel box.

---

### Post by fyo on 2008-05-19
This one apparently crops up regularly. 5% of blocks are reserved for privileged processes, so that logging and the like can continue (for a while) even if "all" the disk space is used.

You can adjust the percentage of blocks reserved by running "tune2fs" with the -m switch on the partition, e.g.

```
$ sudo tune2fs -m2 /dev/sda1
```

This changes the reserved amount to 2% (default being 5%).

---

### Post by lackofcreativity on 2008-05-19
Resized it by about 2 gigs, but it still give me that error on startup and there is still no Applications menu to use to find the source of the problem.

---

### Post by lackofcreativity on 2008-05-19
Found it. It was the result of old Wine programs taking up multiple gigs..

---

### Post by lackofcreativity on 2008-05-20
Apparantly the folder I can't write to is the .dmrc folder in my home folder, and my folders are supposed to have 644 permissions (think that's the number...). Does this help?

---

