---
title: "/tmp loose lost+found"
date: 2016-08-17
forum: General Help
---

### Post by georgesgiralt on 2016-08-17
Hello !
My laptop has an M.2 SSD card onto which I've installed Ubuntu LTS software (at first 14.04, then 16.04 by upgrade).
As I do not want to "use" the SSD too fast, I’ve installed the /var and /tmp on the hard disk with two separate partitions. 
If everything is fine for /var; it is all too different for /tmp which is wiped out at every reboot. And with it the lost+found directory. 
I would like to keep the general behaviour of the /tmp temporary repository but retain the general file system layout of a plain ext4 file system. 
How should I do that ? 
What could be the best solution ? 
Many thanks in advance for your help.

---

### Post by mook765 on 2016-08-17
The cleaning of /tmp is done by the upstart script /etc/init/mounted-tmp.conf. The script is run by upstart everytime /tmp is mounted. Practically that means at every boot.
  The script does roughly the following: if a file in /tmp is older than $TMPTIME days it will be deleted.
  The default value of $TMPTIME is 0, which means every file and directory in /tmp gets deleted. $TMPTIME is an environment variable defined in /etc/default/rcS.

---

### Post by georgesgiralt on 2016-08-19
thank you Mook765 for your answer. 
This scripts seems to avoid removing Lost+found. And this directory is gone... So there is something else or a bug somewhere. 
Adjusting $TMPTIME is not a solution either because, at some time, lost+found will become older than the value of $TMPTIME... 
So for now, I'll recreate the file system on /tmp to get the lost+found directory  back, and see how it survive the various restart of the machines.
Have a nice day.

---

### Post by mook765 on 2016-08-19
Normally there is not a Lost+Found-folder in /tmp.
In your case it will be created there because you made an extra partition for /tmp.
You don't need the lost+found-folder there as /temp holds only temporary files which will be deleted anyway.
You still have a lost+found-folder in each of your other partitions of your system, so in my eyes no reason to worry about...
Kind regards...

---

### Post by georgesgiralt on 2016-08-19
Well, may I respectfully disagree ? 
Ext4 file system *requires* a lost+found directory and mkfs creates it. So it HAS to be there, and deleting it may have some unknown impact on the behaviour of the file system and or system. 
Even if the file system is cleaned at every reboot the underlying software requires it...

---

### Post by mook765 on 2016-08-19
The lost+found-folder will only be used by fsck or e2fsck. When you run fsck on this partition and the lost+found-folder is missing, fsck will create a lost+found-folder.
The lost+found-folder will be created only when fsck find something to place in it.
To create a lost+found-folder you don't need to recreate the file-system.
SImply use this commands```
cd /tmp
mklost+found
```
Please refer to```
man mklost+found
```
Is there a special reason why you want to have /tmp on it's own partition?
If not it might be better to keep /tmp on your root-partition, then you don't need to bother about the lost+found-folder...
I found this script on my system in /etc/init.d/mountnfs-bootclean.sh```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          mountnfs-bootclean
# Required-Start:    $local_fs mountnfs
# Required-Stop:
# Default-Start:     S
# Default-Stop:
# X-Start-Before:    bootmisc
# Short-Description: bootclean after mountnfs.
# Description:       Clean temporary filesystems after
#                    network filesystems have been mounted.
### END INIT INFO

. /lib/lsb/init-functions
. /lib/init/bootclean.sh

case "$1" in
  start|"")
    # Clean /tmp, /var/lock, /var/run
    clean_all
    exit $?
    ;;
  restart|reload|force-reload)
    echo "Error: argument '$1' not supported" >&2
    exit 3
    ;;
  stop|status)
    # No-op
    ;;
  *)
    echo "Usage: mountnfs-bootclean.sh [start|stop]" >&2
    exit 3
    ;;
esac

:

```
There is this line where it says "clean_all", and just right now i was unable to find out where this is defined...
So, that's it for the moment,
kind regards...

---

### Post by mook765 on 2016-08-20
So, at least I found the bug-report for this issue:
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=788193](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=788193)
I also found this:
[https://github.com/systemd/systemd/issues/181](https://github.com/systemd/systemd/issues/181)
In the second link I found this:
> So it seems that the original reporter messed something up: maybe he created the directory as non-root?
You may try to create a lost+found-folder as root:
```
cd /tmp
sudo mklost+found
```
If the lost+found-folder is deleted again during boot-cleanup, you will depend on the developers to change this behavior of the system.
As far as I see, no chance for us end-users to solve that ourself.
We would need more than basic knowledge about programming in C or C++
Anyway, this was a good lesson for me too, 
kind regards...

---

### Post by georgesgiralt on 2016-08-23
So, definitely a bug here.
I recreated the lost+found directory using mklost+found (and sudo as you must be root to create it).
And, guess what, upon reboot, the directory is gone. 
So the system put in place to lean the /tmp is not working and is not configurable either. (all the changes made in  /etc/init/mounted-tmp.conf are useless).

---

### Post by mook765 on 2016-08-23
Yeah, I think the lost+found-folder shouldn't be deleted anyway.
But you are not going to store private data in the /tmp-folder.
Normally, data stored in /tmp will be needed only in the running session, this data will be deleted on next boot, so normally there is nothing left what could be placed in lost+found.
The lost and found-folder is only used by fsck, and you can use fsck on the /tmp-partition when the partition is not mounted, normally this will be done in recovery-mode.
If fsck find something to store in lost+found, fsck will create lost+found if it doesn't exist already. You still have the chance then to recover data...
If you are a normal end-user like I am, i think the not existing lost+found-folder is not going to lead to problems or instability of the system...
I would agree that this might be different if you run a server...
Regards...

---

