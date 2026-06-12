---
title: "[SOLVED] Can't mount CD-ROM"
date: 2008-03-08
forum: General Help
---

### Post by tad1073 on 2008-03-08
I get the ubiquitous "Unable to mount the volume, mount: must be superuser to mount"
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

---

### Post by Rocket2DMn on 2008-03-08
I'm assuming that is your fstab entry, what if you run
```
sudo mount /dev/scd0
```

---

### Post by tad1073 on 2008-03-08
That worked, how can I mount it w/o being root

---

### Post by Rocket2DMn on 2008-03-08
There is a program you can get from the repos called pmount, but the standard way of mounting is using the regular mount command with sudo.  I've never tried pmount for CDs, just USB drives, but it should work.  You may have to specify the mount options using pmount so it doesn't resort to your fstab file, but I'm not entirely sure, you'll just have to try.

---

### Post by tad1073 on 2008-03-08
I guess I will make an alias in .bashrc if that is possible. Something like this:
```

alias cd='sudo mount /dev/scd0'

```

but that didn't work...

When I installed Ubuntu the first time, I was able to pop the cd in and it would automont, all I had to do was open the folder

---

### Post by Rocket2DMn on 2008-03-08
> **tad1073 said:**
> I guess I will make an alias in .bashrc if that is possible. Something like this:
```

alias cd='sudo mount /dev/scd0'

```

but that didn't work...

When I installed Ubuntu the first time, I was able to pop the cd in and it would automont, all I had to do was open the folder

don't alias the cd command, that is for changing directories.  Rather, invent a new one like "mount_cd".  Again, you may have to expand on the command to include other mount options.

---

### Post by unutbu on 2008-03-08
I don't know why this should work, but I've read other threads (
[http://ubuntuforums.org/showthread.php?t=716210&highlight=mount+chown]("http://ubuntuforums.org/showthread.php?t=716210&highlight=mount+chown")
)
for which this was the solution:

```

sudo chown -R username:username /media/cdrom0

```

---

### Post by Rocket2DMn on 2008-03-08
> **unutbu said:**
> I don't know why this should work, but I've read other threads (
[http://ubuntuforums.org/showthread.php?t=716210&highlight=mount+chown]("http://ubuntuforums.org/showthread.php?t=716210&highlight=mount+chown")
)
for which this was the solution:

```

sudo chown -R username:username /media/cdrom0

```

That will only work for filesystems that use permissions that chown can affect, namely ext2/ext3.  CDs have their own filesystem, and since you can't write to a disc that isn't a CD-R, that won't do much good, esp. since CDs are read only anyway.
Using mount options is the appropriate way to mount a filesystem that doesn't use ext2/3 permissions.  For more info, check out How to Fstab - [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by unutbu on 2008-03-08
Umm... sorry, I think I misread the thread... chown is probably not going to solve your problem. 

If you be happy with CDs being automounted, have you tried commenting out
```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```
in /etc/fstab?

---

### Post by tad1073 on 2008-03-09
> **unutbu said:**
> Umm... sorry, I think I misread the thread... chown is probably not going to solve your problem. 

If you be happy with CDs being automounted, have you tried commenting out
```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```
in /etc/fstab?

This works perfectly, thanks for the tip. i throw the cd in and it is mounted automatically.

---

