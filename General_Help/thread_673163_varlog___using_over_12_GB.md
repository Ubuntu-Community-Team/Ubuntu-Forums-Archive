---
title: "/var/log   using over 12 GB"
date: 2008-01-20
forum: General Help
---

### Post by mat10000 on 2008-01-20
I was using PhotoRec on an external hard drive and it ran for over 8 hours.  It didn't recover anything  after the first hour.  I think it stopped working because by hard drive was full.  These file were in /var/log/


Syslog           -  2.3 GB
kern.log         -  2.3 GB
messages     -  2.2 GB
Syslog.0        -  2.3 GB
kern.log.0      -  2.3 GB
messages.0  -  1.3 GB

I can't open any of them because they are too big.

---

### Post by LO Matt on 2008-01-20
That's not good.  Use the tail command in the command line to read the last lines of a given file.  Read the man file to tailor how many lines you want to read.  The default is the last 10 lines.

```
man tail
```

Hopefully they will have error messages in them that you can figure out what's wrong.

---

### Post by mat10000 on 2008-01-20
Alright i tried this

tail -200 /var/log/syslog | less

I don't reall know what it says.   Could i just delete them?

---

### Post by LO Matt on 2008-01-20
> **mat10000 said:**
> Alright i tried this

tail -200 /var/log/syslog | less

I don't reall know what it says.   Could i just delete them?

Yes.  However, those logs contain the info that might solve your problem.  Try searching google with the error messages, maybe it'll lead to fixing the problem w/ PhotoRec?

---

### Post by mat10000 on 2008-01-20
I copied those files to an external hard drive and deleted them, but now the Disk free space is wrong

Am i missing something?

[IMG]http://img340.imageshack.us/img340/483/screenshotwx0.png[/IMG]

---

### Post by LO Matt on 2008-01-20
Weird,  4.2 Gb used yet it says 16.9 used on top.  Goto Edit-Preferences and make sure it's scanning all the mount points for that drive.  That's about all I can think of.

edit: check if /root/.Trash folder is empty.  From [https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/114341](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/114341)  apparently trash owned by root is not scanned by Disk Utility.  If you had to delete w/ sudo, this could be it.

---

### Post by mat10000 on 2008-01-20
thanks dude, i had no idea that was there.

---

