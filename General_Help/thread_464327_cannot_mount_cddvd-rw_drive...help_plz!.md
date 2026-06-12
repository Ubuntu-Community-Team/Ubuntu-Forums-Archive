---
title: "cannot mount cd/dvd-rw drive...help plz!"
date: 2007-06-04
forum: General Help
---

### Post by kdarkentity on 2007-06-04
i put a cd that has an old windows game on it into my laptop running feisty and now my cd drive will not mount

---

### Post by Shazaam on 2007-06-04
A couple of stupid questions...
Is the cd still in the drive?
Is the cd a re-writable disk?
Have you rebooted your pc?

---

### Post by kdarkentity on 2007-06-04
the cd is not in the drive

the cd is not rw

yes i have rebooted

and no matter what cd i insert my drive will not mount

---

### Post by DeathStar on 2007-06-06
Hi,

Not sure if it's the same issue, but I had a problem with DVD's not mounting.

[[COLOR="Blue"]TRY THIS[/COLOR]]("http://ubuntuforums.org/showthread.php?p=2794119#post2794119")

---

### Post by n3twrkm4n on 2007-06-07
> **kdarkentity said:**
> i put a cd that has an old windows game on it into my laptop running feisty and now my cd drive will not mount

I was having issues getting a DVD to mount... I did notice one thing...

Take a look at /etc/fstab (vim /etc/fstab)...

My cdrom was listed as the following:
/dev/hda     /media/cdrom0 /udf,iso9660 user,noauto   0   0

It should be listed as
/dev/scd1    /media/cdrom0 /udf,iso9660 user,noauto   0   0


That fixed me not being able to mount, of course a "shutdown -r now" would be recommended ;)

I just wanted to post what I had because I stumbled on this post, and I'm sure others might have this problem as well.

---

### Post by kdarkentity on 2007-06-07
thanks but i already have my dvd drive working correctly ...for the moment anyways lol

---

