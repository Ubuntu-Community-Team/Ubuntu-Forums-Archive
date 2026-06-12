---
title: "How do you make /tmp buffer larger?"
date: 2013-01-21
forum: General Help
---

### Post by accumbare on 2013-01-21
I would like to reopen the thread because I have a similar problem with my /tmp directory. I am not quite sure if the solution has already been discussed in the thread.
My /tmp dir has a quota of 1MB:

```

Filesystem                     Size  Used Avail Use% Mounted on
/dev/mapper/srv--lin--02-root  228G   15G  202G   7% /
udev                           974M   12K  974M   1% /dev
tmpfs                          395M  400K  394M   1% /run
none                            50M  204K   50M   1% /run/lock
none                           986M  8,0K  986M   1% /run/shm
overflow                       1,0M   52K  972K   6% /tmp
/dev/sda1                      228M  151M   65M  70% /boot


```

How d I change the size of tmp ?

Thank you very much!

---

### Post by oldos2er on 2013-01-21
Original thread: [http://ubuntuforums.org/showthread.php?t=1431169](http://ubuntuforums.org/showthread.php?t=1431169)

Post moved to its own thread.

---

### Post by SeijiSensei on 2013-01-21
I have no idea what "overflow" is, but look at /etc/fstab and see if there is a line there that include /tmp as the mount point.  If so use "sudo nano /etc/fstab" and put a hash mark ("#") at the beginning of that line.  Use Ctrl-X to save the file and exit, then reboot.

Now /tmp should just be another directory under the root and will have full access to those gigabytes of unused space.

I'm just curious, but how did you end up with a system like this?  By default /tmp is just a directory with no mounted filesystem.  Even more curious is the notion that it should be limited to just a megabyte of storage.  I have hardly anything in /tmp except the directories and files things like KDE and pulseaudio create, and they constitute 0.6 megs.  Any reasonably large file stored there would easily break a one megabyte quota.

---

