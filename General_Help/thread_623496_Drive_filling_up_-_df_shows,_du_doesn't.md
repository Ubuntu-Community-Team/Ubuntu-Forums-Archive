---
title: "Drive filling up - df shows, du doesn't"
date: 2007-11-25
forum: General Help
---

### Post by mitchm on 2007-11-25
My hard drive is filling up rapidly all of a sudden.  As you can see by the output below, df is showing much of the drive being filled, but du doesn't show any files taking the space.  du output has remained the same, but df output is constantly growing.  This is going to kill my server soon.

Any ideas?  I saw some posts about similar problems but no solutions:

/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.9G  2.4G  7.0G  26% /
varrun                3.8G   92K  3.8G   1% /var/run
varlock               3.8G     0  3.8G   0% /var/lock
udev                  3.8G   36K  3.8G   1% /dev
devshm                3.8G     0  3.8G   0% /dev/shm
/dev/md0              191G   61G  131G  32% /mnt

/# du -h --max-depth=1 /
816K    /boot
4.0K    /srv
15G     /mnt
88K     /root
418M    /usr
17M     /lib
7.6G    /proc
4.0K    /opt
160M    /var
3.9M    /etc
6.4M    /sbin
0       /sys
4.0M    /bin
16K     /lost+found
40K     /dev
4.0K    /initrd
136K    /home
1.7G    /tmp
25G     /

---

### Post by hikaricore on 2007-11-25
Check your home directory (including hidden) for insanely large files.

Every so often bugs have caused files like .xsession-errors to grow into multi-gigabyte sizes.  >.<

---

### Post by mitchm on 2007-11-25
I figured out the cause and a workaround, but not the solution.

I have a daemon that copies a large file (search index), then deletes the old version.  It does this a lot more often now.

lsof revealed that all the deleted files were still "open", even though lsof shows them as deleted.

I'm not sure why that is.  Might be that the application (ruby) is not releasing the file when it is deleting it or that the search index is keeping the file open.  I'll have to look into that.

Regardless, when I restart that daemon, all of the space is immediately freed.  I can just restart the daemon every so often until I figure out how to properly "release" the file.

Any suggestions would be appreciated.  I'm using Ruby/Rails and a Ferret dRB server, if that means anything to anyone here.

---

### Post by bingoUV on 2007-11-26
Linux kernel will not release the space for a file as long as it is open by at least one application. Rest of the applications will not be able to see the file, but it will keep occupying space until the application "close"s the file.

You need to application to behave properly. If they are two or more applications, they need to be friendly to each other too.

---

