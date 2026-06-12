---
title: "Mounted my files to oblivion"
date: 2008-03-18
forum: General Help
---

### Post by madsun on 2008-03-18
Today I decided to go 100% linux filesystems on my server, so i started copying files around my server witch had two ntfs partitions. In order to convert them to ext3 i had to move the files around a bit. Somewhere in this mess I managed to mount a partition somewhat wrong, so the result was that i filled up my system partition. Now, i've filled up a 320gb drive (before this it was using about 20gb), but i cannon locate the files...(I belive this has something to do with me mounting the partitions wrong or something..)

How can I locate my files? I've tried with "find" without any luck..

df
```

root@mediaserver:/home# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            306367028 306084436         0 100% /
varrun                  224880       180    224700   1% /var/run
varlock                 224880         0    224880   0% /var/lock
udev                    224880        72    224808   1% /dev
devshm                  224880         0    224880   0% /dev/shm
/dev/sdc1            307663800 116851452 175183916  41% /media/sdc
overflow                  1024         0      1024   0% /tmp
/dev/sdb1            307663800  85356656 206678712  30% /media/sdb


```

df -i
```

root@mediaserver:/home# df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1            38912000   65206 38846794    1% /
varrun                 56220      41   56179    1% /var/run
varlock                56220       1   56219    1% /var/lock
udev                   56220    2854   53366    6% /dev
devshm                 56220       1   56219    1% /dev/shm
/dev/sdc1            39075840     190 39075650    1% /media/sdc
overflow               56220       7   56213    1% /tmp
/dev/sdb1            39075840    4817 39071023    1% /media/sdb

```

/dev/sda1 contains the files..its 100% full, and im pretty sure that my files are there (mainly my cd collection in flac)

any clues?

---

### Post by nick_h on 2008-03-18
The *find* command should work.  You could also try the *locate* command.

How are you trying to find the files?  by filename?

Try:
```
sudo find / -name "*.flac" -print
```
to find all files matching *.flac

You could also try the -mmin option to find files modified within a certain number of minutes.

Type:
```
man find
```
for the manual page.

---

### Post by madsun on 2008-03-18
I've tried find with both timefilters and size filters. Some of the files are pretty large, so i've tried find / -name '*' -size +100000k. Nothing comes up :| So.. since sda1 is 100% full, they should be there somewhere..or is this another problem, and ive actually deleted all my files?

---

### Post by HermanAB on 2008-03-18
Well, there are a number of possibilities:
1. The partition with your missing files is not mounted at all
2. The partition is overmounted by something else and is unreachable

You can see what is mounted with the 'mount' command:
$ sudo mount

You can unmount partitions with:
$ sudo umount /mnt/whatever

Note that if you double mount things on a single mount point, only the last one will be reachable.

Cheers,

Herman

---

### Post by madsun on 2008-03-18
But..since my sda1 partition is all ext3 (and been so before i started converting the other partitions) AND this partition is 100% full..shouldnt the files show up? /dev/sda1 is the only thing here..i wanna list all the files on that partition and figure out 
1. what's the cause of that it is 100% full
2. locate my files

ls -a to find hidden files doesnt give anything.. ls -R -a same thing.

mount gives.. 
```

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sdc1 on /media/sdc type ext2 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)
/dev/sdb1 on /media/sdb type ext2 (rw)

```

---

### Post by nick_h on 2008-03-18
> ls -a to find hidden files doesnt give anything.. ls -R -a same thing.
Try:
```
sudo ls -a /
```

---

### Post by madsun on 2008-03-18
Tried that...
sudo ls -a -R / | grep flac gives nothing :(

---

### Post by nick_h on 2008-03-19
Unfortunately it appears that the files you are looking for do not exist on that filesystem.

---

### Post by pointone on 2008-03-19
Try "du / -h --max-depth=1"; this will show you the size of each directory. If you see one that's abnormally large, du it as well. For instance, if it turns out /lib is taking up 200 GB, run "du /lib -h --max-depth=1", and find the largest subdirectory. Repeat until you find what you're looking for. You could also use the Disk Usage Analyzer (Applications > Accessories) for a graphical equivalent.

---

