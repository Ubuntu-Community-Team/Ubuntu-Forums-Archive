---
title: "Odd drive/folder renaming problem"
date: 2008-05-21
forum: General Help
---

### Post by dartmusic on 2008-05-21
I'm running Hardy on a P4 3.6HT proc with 1GB of RAM.  

Yesterday I ran into the oddest thing I've seen yet with Ubuntu.  I'm not sure what I did or how I did it (though it would have been indirectly and I think because of something I did with Azureus, though not certain), but here's what happened:  I have two drives of TV shows and movies.  The drive that movies are on is called Big_Boy (at the time it was the largest drive I had) in a folder called Movies.  TV shows are on Little_Big_Boy (which was superceded by BB and hence renamed) in a folder called TV.  When I download torrent files, I download them to /media/Little_Big_Boy/TV/_torrents.  Yesterday I set Azureus to automatically launch new torrents in the _torrents folder.  (I added the underscore so that it would be at the top of the list when browsing on my MacBook.)  After I made this change, browsing to /media/Little_Big_Boy/TV shows only one folder, the _torrents folder, which only shows torrents downloaded since I made this change.  And now there is another drive which is listed as /media/Little_Big_Boy_ (an underscore added to the end of the name).  This drive has a folder called TV which seems to hold all of my TV episodes.

Obviously I don't want two drive designations, nor do I need two folders.  I can rename Little_Big_Boy, but can't rename Little_Big_Boy_; I get an error saying that the folder is in use and cannot be changed.  I've tried rebooting, to no avail.

I'm not sure exactly how or why this happened, but would really like to put things back the way they were without too much trouble.  

Any ideas?

Thanks!

---

### Post by dartmusic on 2008-05-22
Bump...really?  No one has any idea?  I really don't want to have to copy/reformat/etc.  Anybody?:confused:

---

### Post by anystupidname on 2008-05-22
How about a couple outputs?
"df -ah"
"fdisk -l"
"du"
"ls -hasl"
...?
so we can try to understand your scenario better?

---

### Post by dartmusic on 2008-05-22
Here you go:

df -ah
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             273G  109G  151G  42% /
proc                     0     0     0   -  /proc
/sys                     0     0     0   -  /sys
varrun                506M  124K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   80K  506M   1% /dev
devshm                506M   12K  506M   1% /dev/shm
devpts                   0     0     0   -  /dev/pts
lrm                   506M   38M  468M   8% /lib/modules/2.6.24-17-generic/volatile
securityfs               0     0     0   -  /sys/kernel/security
rpc_pipefs               0     0     0   -  /var/lib/nfs/rpc_pipefs
nfsd                     0     0     0   -  /proc/fs/nfsd
binfmt_misc              0     0     0   -  /proc/sys/fs/binfmt_misc
/dev/sdb1             187G  186G  1.2G 100% /media/Little_Big_Boy_
/dev/sdc1             459G  432G  3.8G 100% /media/Big_Boy
/dev/sdd1             459G  431G  4.8G  99% /media/disk
gvfs-fuse-daemon      0.0K  0.0K  0.0K   -  /root/.gvfs
/dev/sde1             230G  120G   98G  56% /media/backup

fdisk -l /media/Little_Big_Boy
last_lba(): I don't know how to handle files with mode 40755

fdisk -l /media/Little_Big_Boy_
last_lba(): I don't know how to handle files with mode 40777

du /media/Little_Big_Boy
4    /media/Little_Big_Boy/TV/_torrents
8    /media/Little_Big_Boy/TV
12    /media/Little_Big_Boy

du /media/Little_Big_Boy_
lists every folder that's supposed to be in the above named drive

ls -hasl /media/Little_Big_Boy
total 12K
4.0K drwxr-xr-x  3 rickstone rickstone 4.0K 2008-05-21 07:29 .
4.0K drwxrwxrwx 11 rickstone rickstone 4.0K 2008-05-22 07:06 ..
4.0K drwxr-xr-x  3 rickstone rickstone 4.0K 2008-05-21 07:29 TV

ls -hasl /media/Little_Big_Boy_
total 92K
4.0K drwxrwxrwx  8 rickstone  rickstone 4.0K 2007-02-18 14:44 .
4.0K drwxrwxrwx 11 rickstone  rickstone 4.0K 2008-05-22 07:06 ..
4.0K drwxrwxrwx  2 root       root      4.0K 2006-11-13 22:04 lost+found
4.0K drwxrwxrwx  4 rickstone  rickstone 4.0K 2006-08-24 20:17 .Trash-1000
4.0K drwxrwxrwx  2 polkituser       116 4.0K 2006-11-11 18:50 .Trash-mythtv
 60K drwxrwxrwx  2 rickstone  rickstone  56K 2008-04-24 22:28 .Trash-rickstone
4.0K drwxrwxrwx  4 root       root      4.0K 2007-01-01 10:02 .Trash-root
8.0K drwxrwxrwx 81 rickstone  rickstone 8.0K 2008-05-19 17:41 TV

---

### Post by anystupidname on 2008-05-22
Lets have your /etc/fstab and the mount output also.

First guess, I'd say /dev/sdb1 (aka normally mounted as Little_Big_Boy) was unmounted at one point for whatever reason and the _torrents folder was created at that time (not actually on the right mount point). Then you rebooted or the drive somehow got remounted and created the Little_Big_Boy_ folder because the other folder already existed and was already mounted?!?

Tell me if that sounds likely to you. Once I see the fstab and mount output, it should be easier to figure out what to do. Probably:
-move _torrent contents to temporary location
-umount both
-mount /dev/sdb1 back to the right mount point (rename if necessary)
-move _torrent back to where you had intended to have it
-cleanup

---

### Post by dartmusic on 2008-05-22
I think that your theory is probably/possibly correct.  Just another *nix oddity.  I've seen things like this before but not for quite some time.

I deleted the incorrect /TV/_torrents folder(s), umounted everything that could then forced /dev/sdb1 to /media/Little_Big_Boy and everything worked as it should.

Thanks so much for the help/hints/etc.!

Have a great weekend.

---

### Post by lemming465 on 2008-05-23
Actually, I have heard of a couple of other people with the mount point mutating with trailing _ problem.  So I'm pretty sure there is an actual bug lurking there somewhere; this is apparently something the systems is doing to the users, not something the users are doing to the system.

---

