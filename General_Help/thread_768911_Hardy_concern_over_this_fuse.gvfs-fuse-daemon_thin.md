---
title: "Hardy: concern over this fuse.gvfs-fuse-daemon thing"
date: 2008-04-26
forum: General Help
---

### Post by svaens on 2008-04-26
Hi guys, 

Let me just begin by saying, I have just installed (clean) the new Hardy distribution of Ubuntu, and I am really impressed so far by the improvements i've seen so far, so far as compatibility with my old system is. Even Compiz is working! 

All installed, and no hitches. 

Then I decided i'd like to have my home on a separate partition. I followed the instructions found on this thread: 
[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

All worked fine. However, There is one strange thing that concerns me... 
And although I have not as yet experienced any ill effects due to this, it looks..... wrong. And I am a little worried. 


I have attached an image of my System Monitor. 
For those who can't view it, 
It lists my two partitions as normal

/dev/sda5   /            (my main ubuntu root partition) 
/dev/sda3   /home        (my extra partition for home)

BUT there is this funny entry:

dvfs-fuse-daemon /home/sean/.gvfs fuse.gvfs-fuse-daemon. 

That wouldn't normally alarm me too much, obviously it is some daemon which I haven't read about yet.... but what DOES alarm me, is that, ALTHOUGH I moved my home to the sda3 partition, 
the details of disk size etc mentioned with the gvfs-fuse-daemon entry match those of my original root partition, NOT the new partition where home actually resides now. 

How can this be? I don't understand what is going on here!

Here is a copy of my fstab file.... just in case you are interested.. 



```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=8e58c507-b42f-432f-8d75-aff0602b74c3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=02f58d1f-4509-4207-a2db-0ee14a5aff6b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda3 /home ext3 defaults,errors=remount-ro 0 1


```

---

### Post by timebomb on 2008-04-26
Bump. I'm seeing the same thing and found this post when I started investigating.

---

### Post by misterfixit on 2008-04-30
Noticed what happened to my system ...

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             220G  219G     0 100% /
varrun                2.0G  248K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G   76K  2.0G   1% /dev
devshm                2.0G   12K  2.0G   1% /dev/shm
lrm                   2.0G   43M  1.9G   3% /lib/modules/2.6.24-16-generic/volatile
overflow              1.0M   40K  984K   4% /tmp
/dev/sdd1              32M  1.8M   30M   6% /media/disk
/dev/sde1             1.9G  1.1G  744M  59% /media/disk-1
gvfs-fuse-daemon      220G  219G     0 100% /root/.gvfs
/dev/sdb1             189G   96G   84G  54% /media/disk-2


I've been working with the 64-bit forum folks on this issue ...

Wonder if this is the culprit and if I delete /root/.gvfs it will solve the problem???

TIA

Dave

---

### Post by bodhi.zazen on 2008-04-30
See this thread :

[http://ubuntuforums.org/showthread.php?t=748778](http://ubuntuforums.org/showthread.php?t=748778)

---

### Post by misterfixit on 2008-04-30
> **bodhi.zazen said:**
> See this thread :

[http://ubuntuforums.org/showthread.php?t=748778](http://ubuntuforums.org/showthread.php?t=748778)

Interesting and looks like what has hosed my system.  However, any changes I make to the baobab preferences are not saved.  I've booted as root and changed preferences as well as booting as user dave.  Man baobab has no mention of command line access to the application except that command line invoking baobab results in exactly the same gui and failure to retain preferences.

Also, the .gvfs file cannot be deleted; I am going to try booting from the live cd and see if I can kill it that way.  Umount does not work as attempted del of .gvfs shows error "in use" (which it probably is).

Baobab cannot be deleted without damage to the ubuntu-desktop.

Catch 22?

This is a major problem for me right now.  I beg guidance on how I can fix this issue.

Thank you,

Dave

---

### Post by bodhi.zazen on 2008-04-30
unmount it with -l

sudo umount -l /root/.gvfs
sudo umount -l ~/.gvfs

you may need to unmount specific directories in .gvfs

After it is unmounted, then change your options.

If that fails -> Launchpad (Search & Bug report)

---

