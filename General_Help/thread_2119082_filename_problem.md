---
title: "filename problem"
date: 2013-02-22
forum: General Help
---

### Post by resakse on 2013-02-22
I used rsync to backup my itunes collection from my windows 7 machine through samba into my ubuntu server, but turn out I can't delete the file due to filename problem.

```
resakse@radius:/media/storage/Musics/iTunes/iTunes/iTunes Music/Music/Linkin Park/Linkin Park$ ls -al
ls: cannot access .Esaúl.mp3.mWfaV6: No such file or directory
ls: cannot access .Esaúl.mp3.npPRoW: No such file or directory
total 0
drwxrwxrwx 2 resakse resakse 48 Feb 22 20:03 .
drwxrwxrwx 3 resakse resakse 80 Feb 22 20:03 ..
?????????? ? ?       ?        ?            ? .Esa??l.mp3.mWfaV6
?????????? ? ?       ?        ?            ? .Esa??l.mp3.npPRoW
resakse@radius:/media/storage/Musics/iTunes/iTunes/iTunes Music/Music/Linkin Park/Linkin Park$ 

```

```
resakse@radius:/media/storage/Musics/iTunes/iTunes/iTunes Music/Music/Linkin Park/Linkin Park$ rm -fr *
resakse@radius:/media/storage/Musics/iTunes/iTunes/iTunes Music/Music/Linkin Park/Linkin Park$ ls -al
ls: cannot access .Esaúl.mp3.mWfaV6: No such file or directory
ls: cannot access .Esaúl.mp3.npPRoW: No such file or directory
total 0
drwxrwxrwx 2 resakse resakse 48 Feb 22 20:03 .
drwxrwxrwx 3 resakse resakse 80 Feb 22 20:03 ..
?????????? ? ?       ?        ?            ? .Esa??l.mp3.mWfaV6
?????????? ? ?       ?        ?            ? .Esa??l.mp3.npPRoW
resakse@radius:/media/storage/Musics/iTunes/iTunes/iTunes Music/Music/Linkin Park/Linkin Park$ 

```

```
resakse@radius:/media/storage/Musics/iTunes/iTunes/iTunes Music/Music/Linkin Park$ rm -fr Linkin\ Park/
rm: cannot remove `Linkin Park': Directory not empty


```


the file name are actually in utf8, so convmv wont convert it..

```
resakse@radius:/media/storage/Musics/iTunes/iTunes/iTunes Music/Music/Linkin Park/Linkin Park$ python
Python 2.7.3 (default, Aug  1 2012, 05:16:07) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import chardet
>>> import os  
>>> 
>>> for n in os.listdir('.'):
...     print '%s => %s (%s)' % (n, chardet.detect(n)['encoding'], chardet.detect(n)['confidence'])
... 
.Esaúl.mp3.mWfaV6 => utf-8 (0.505)
.Esaúl.mp3.npPRoW => utf-8 (0.505)
>>> 
```

btw, I got tons of this kinda files on my server, it taking out space and I can't delete it.

---

### Post by duke.tim on 2013-02-23
Strange problem, I've had a similar problem in the past but forcing the removal fixed it.

Try running "fsck" on the disk and see what happens. If the anomalies are still there try removing the files again after fsck.
(if it is an NTFS or other MS file system "chkdsk" instead)


Just out of curiosity what does 'lsattr filename' return?

If that doesn't work start experimenting?
I have no clue of what the consequences of this could be so proceed at your own risk
```
actualfile.txt > corruptfile
```
If it works, that should pipe/overwrite the file with the valid file, then you can try deleting it.

---

### Post by papibe on 2013-02-23
Hi resakse.

It looks like like the code you posted is:
[LIST]
[*]run on the server itself, and
[*]the disk were the data resides is an external drive.
[/LIST]
Is that right?
What kind of filesystem the disk has?

Could you post the results of these commands?
```
mount -l

locale
```
Regards.

---

### Post by resakse on 2013-02-24
> **duke.tim said:**
> Strange problem, I've had a similar problem in the past but forcing the removal fixed it.

Try running "fsck" on the disk and see what happens. If the anomalies are still there try removing the files again after fsck.
(if it is an NTFS or other MS file system "chkdsk" instead)


Just out of curiosity what does 'lsattr filename' return?

If that doesn't work start experimenting?
I have no clue of what the consequences of this could be so proceed at your own risk
```
actualfile.txt > corruptfile
```
If it works, that should pipe/overwrite the file with the valid file, then you can try deleting it.


fsck returns  no problem with the disc :(


```
resakse@radius:/media/storage/Musics/iTunes/iTunes Music/Music/Jason Derulo$ ls -l
ls: cannot access Jason DerÃ¼lo: No such file or directory
total 0
?????????? ? ? ? ?            ? Jason DerÃ¼lo
resakse@radius:/media/storage/Musics/iTunes/iTunes Music/Music/Jason Derulo$ lsattr Jason\ DerÃ¼lo
lsattr: No such file or directory while trying to stat Jason DerÃ¼lo
resakse@radius:/media/storage/Musics/iTunes/iTunes Music/Music/Jason Derulo$

```

---

### Post by resakse on 2013-02-24
> **papibe said:**
> Hi resakse.

It looks like like the code you posted is:
[LIST]
[*]run on the server itself, and
[*]the disk were the data resides is an external drive.
[/LIST]
Is that right?
What kind of filesystem the disk has?

Could you post the results of these commands?
```
mount -l

locale
```
Regards.

hi!

actually the disk is on the server..
I'm using reiserfs for the filesystem and flexraid.

```
resakse@radius:/media/storage/Musics/iTunes/iTunes Music/Music/Jason Derulo$ mount -l
/dev/sde1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sde6 on /home type ext4 (rw)
rpc_pipefs on /run/rpc_pipefs type rpc_pipefs (rw)
/dev/sda1 on /root/FlexRAID-Managed-Pool/class1_0/{e9979cbb-21df-4c9d-a7c1-20d4112145c1} type reiserfs (rw,nosuid,nodev)
/dev/sdb1 on /root/FlexRAID-Managed-Pool/class1_0/{21d9b61b-e5df-4f20-b9e2-9311be73c6d3} type reiserfs (rw,nosuid,nodev)
/dev/sdc1 on /root/FlexRAID-Managed-Pool/class1_0/{97feed82-d2a5-4400-8e72-d99a09b9f07e} type reiserfs (rw,nosuid,nodev)
/dev/sdd1 on /root/FlexRAID-Managed-Pool/class1_0/{4197c7ac-41ef-4baa-a316-6659f8e64c4b} type reiserfs (rw,nosuid,nodev)
FlexRAIDFS on /media/storage type fuse.FlexRAIDFS (rw,nosuid,nodev,allow_other)


```

```
resakse@radius:/media/storage/Musics/iTunes/iTunes Music/Music/Jason Derulo$ locale
LANG=en_US.UTF-8
LANGUAGE=en_US:en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

```

do you think this if I stop the flexraid array, I can fix the file using convmv?

---

### Post by papibe on 2013-02-24
Thanks.

I have no experience with reiserfs nor flexraid.

But I tested this using ext4, and it works as long as your locale is set to support utf-8.

Since yours is set that way, I would put my attention to the filesystem.

I would try to add an utf-8 mounting option to either the reiser filesystems or the raid itself.

At this moment, I haven't found a way to do it on raiserfs.

Just some thoughts.
Regards.

---

