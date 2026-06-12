---
title: "i can't write on partition /media/hdb1 with ext3 format"
date: 2007-01-28
forum: General Help
---

### Post by jfca283 on 2007-01-28
i connected my new Hard Disc and i obtained some troubles
this was the first
1º at the start i get a message in a console saying 
 unexpected inconsistency
run fsck manually

this error refers to the Disc with ext3 format

well, i did the fsck -f /dev/hdb1 
then the problem with the message  was resolved, but in gnome i went to
/media/hdb1 and i couldn't write, in spite of, edit the fstab of this way
 ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1[B]
/dev/hdb1       /media/hdb1     ext3    auto,users,rw 0 0    [/B]
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
```
 
so, how can i fix this problem?
i've edited the fstab file a lot of times but the problem doesn't go...
thanks for the help...

---

### Post by taurus on 2007-01-28
I would change the entry in /etc/fstab back to

```
/dev/hdb1       /media/hdb1     ext3    defaults   0    1 
```
Since it's ext3, you just have to change the ownership of /media/hdb1 to your login name so you can write to it.

```
sudo chown -R **username**:**username** /media/hdb1
(replace **username** with the actual name that you log in with)
ls -la /media
```

---

### Post by jfca283 on 2007-01-28
> sudo chown -R username:username /media/hdb1
(replace username with the actual name that you log in with)
ls -la /media

mi user name is juan, so, how the commando should go?

sudo chown -R username:juan /media/hdb1
ls -la /media

is that right?

---

### Post by taurus on 2007-01-28
```

sudo chown -R **juan**:**juan** /media/hdb1
ls -la /media

```

---

### Post by jfca283 on 2007-01-28
thnaks a lot taurus
this was the only solution in all the websites i visited, and is not joke...
thanks again, and again, and ....

---

### Post by taurus on 2007-01-28
I see that you can write to /media/hdb1 as juan now.  Have fun and try not to fill up that harddrive, okay!  ;)

---

