---
title: "mount: must be superuser to use mount"
date: 2007-08-28
forum: General Help
---

### Post by slyyy on 2007-08-28
I'm having problems getting my cdrom drive to mount without superuser permission.

I've looked at multiple forum posts on this subject and most problems tend to be with /etc/fstab and the 'user' option missing from the cdrom entry.

However I don't think that is my problem. 

Here is what my /etc/fstab file looks like:

---

proc /proc proc defaults 0 0
# Entry for /dev/hdc1 :
UUID=0638f2b0-f535-4cdd-81d9-52f176ddf53c / ext3 defaults,errors=remount-ro 0 1
/dev/disk/by-uuid/92D8C012D8BFF319 /media/hdc2 ntfs-3g defaults,locale=en_CA.UTF-8 0 0
# Entry for /dev/hdc3 :
UUID=c399e185-54cc-40b0-844f-ab58653ef608 none swap sw 0 0
**/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0**
nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0
/dev/hdc2 /home ext3 nodev,nosuid 0 2

---

When I try:

slyyy@slyyy-htpc:~$ mount /dev/hda /media/cdrom0

I get:

mount: must be superuser to use mount

I can mount no problem if I use 'sudo mount /dev/hda /media/cdrom0'.

What should I be looking at next?

---

### Post by nbkr on 2007-08-28
Try mount /media/cdrom0 (without the /dev/hda).

---

### Post by slyyy on 2007-08-28
Same thing if I try 'mount /media/cdrom0' or try to mount through the GUI.

---

### Post by nbkr on 2007-08-28
> **slyyy said:**
> 
```

proc /proc proc defaults 0 0
# Entry for /dev/hdc1 :
UUID=0638f2b0-f535-4cdd-81d9-52f176ddf53c / ext3 defaults,errors=remount-ro 0 1
/dev/disk/by-uuid/92D8C012D8BFF319 /media/hdc2 ntfs-3g defaults,locale=en_CA.UTF-8 0 0
# Entry for /dev/hdc3 :
UUID=c399e185-54cc-40b0-844f-ab58653ef608 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
**nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0**
/dev/hdc2 /home ext3 nodev,nosuid 0 2

```


Where is the highlighted line from? Maybe this is causing the problem.

---

### Post by slyyy on 2007-08-28
> **nbkr said:**
> Where is the highlighted line from? Maybe this is causing the problem.

I highlighted it in the forum post to show which line concerns the cd-rom he he.

---

### Post by nbkr on 2007-08-28
Have a look at my last post again - I highlighted a different line - the one below the /dev/hda .

---

### Post by slyyy on 2007-08-28
Okay I removed that line. The problem persists.

proc /proc proc defaults 0 0
# Entry for /dev/hdc1 :
UUID=0638f2b0-f535-4cdd-81d9-52f176ddf53c / ext3 defaults,errors=remount-ro 0 1
/dev/disk/by-uuid/92D8C012D8BFF319 /media/hdc2 ntfs-3g defaults,locale=en_CA.UTF-8 0 0
# Entry for /dev/hdc3 :
UUID=c399e185-54cc-40b0-844f-ab58653ef608 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc2 /home ext3 nodev,nosuid 0 2

---

### Post by gletob on 2007-08-29
why cant you just use sudo and "mount /media/cdrom wouldn't work because it dosent specify anything to mount

---

### Post by slyyy on 2007-08-29
I *can* use sudo but I don't want to have to resort to the command line every time I insert a CD into my cd-rom drive.

---

### Post by bmorency on 2007-08-29
i am just wondering. why is your cd-rom drive /dev/hda?  isn't the hard drive usually  /hda?

also, how about trying to mount /dev/cdrom /media/cdrom0

do you know if your user is part of the cdrom group?

---

### Post by slyyy on 2007-08-29
> **bmorency said:**
> i am just wondering. why is your cd-rom drive /dev/hda?  isn't the hard drive usually  /hda?

also, how about trying to mount /dev/cdrom /media/cdrom0

I have no idea.

---

### Post by bmorency on 2007-08-29
did you try this mount command?

mount /dev/cdrom /media/cdrom0


check to see if you are part of the "cdrom" group too.

typing "groups" at the terminal will tell you.

---

### Post by slyyy on 2007-08-29
> **bmorency said:**
> did you try this mount command?

mount /dev/cdrom /media/cdrom0


check to see if you are part of the "cdrom" group too.

typing "groups" at the terminal will tell you.

'mount /dev/cdrom /media/cdrom0' returns the same thing: 'mount: must be superuser to use mount'.

I typed in 'groups' and yes I am in the cdrom group.

---

### Post by kuja on 2007-08-29
> **bmorency said:**
> i am just wondering. why is your cd-rom drive /dev/hda?  isn't the hard drive usually  /hda?

also, how about trying to mount /dev/cdrom /media/cdrom0

do you know if your user is part of the cdrom group?

Two ways that can be, either it's first on the first cable, or, more likely, the hard disks are SATA.

---

### Post by kuja on 2007-08-29
Another thing for you to check, what are the permissions on the cdrom device. Here's what mine are:

blackwaltz@terra:~$ ll /dev/hda
brw-rw---- 1 root cdrom 3, 0 2007-08-21 09:11 /dev/hda

---

### Post by slyyy on 2007-08-29
> **kuja said:**
> Another thing for you to check, what are the permissions on the cdrom device. Here's what mine are:

blackwaltz@terra:~$ ll /dev/hda
brw-rw---- 1 root cdrom 3, 0 2007-08-21 09:11 /dev/hda

I have the same permissions:

slyyy@slyyy-htpc:~$ ls -l /dev/hda
brw-rw---- 1 root cdrom 3, 0 2007-08-28 22:34 /dev/hda

---

### Post by kalahari875 on 2008-01-27
I am having this same problem intermittently with Gutsy. Last night, I inserted a CD/DVD and it mounted on its own. Today, without rebooting or anything changing, I get the 'must be superuser to use mount' error.

My user account is in the cdrom group. The permissions on the CD/DVD devices are:

brw-rw---- 1 root cdrom 11, 0 2008-01-24 19:18 /dev/scd0
brw-rw---- 1 root cdrom 11, 1 2008-01-24 19:18 /dev/scd1

The fstab lines are:

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0

Nothing out of the ordinary here. I bet if I reboot I can mount again.

Any ideas?

---

### Post by seventhc on 2008-02-05
heres mine
```
/media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```
mine has *exec*, maybe you need to add that in.

---

### Post by kalahari875 on 2008-02-07
Nah, turns out it was [this bug]("http://ubuntuforums.org/showthread.php?t=289415"). After I ran my script to correct permissions, all was well.

---

