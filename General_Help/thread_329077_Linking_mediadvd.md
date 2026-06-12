---
title: "Linking /media/dvd"
date: 2006-12-31
forum: General Help
---

### Post by Abaddon on 2006-12-31
Hi all,

Just a quick question - I have a CD-RW and a DVD-burner in my system.  They are mounted as /media/cdrom0 and /media cdrom1

There is a link to /media/cdrom0 called /media/cdrom - which is fine.

I'd like to add a link to /media/cdrom1 called /media/dvd

mainly because whenever I go to open up the DVD, i always manage to open the CDRW instead, and this way I'd have a link for CD and one for DVD.  Easy.

Except ln gives the following:

```
root@ubuntu:/media# sudo ln -dF cdrom1 dvd
ln: creating hard link `dvd' to `cdrom1': Operation not permitted
```

ln's man pages are similarly unhelpful - 

 > -d, -F, --directory
              allow  the  superuser  to  attempt to hard link directories (note: will probably fail due to system restrictions, even for the
              superuser)


So how do I bypass these system restrictions?

Cheers.

---

### Post by jpkotta on 2007-01-01
You don't want a hard link, you want a symlink, enabled by the -s option.```
sudo ln -s cdrom1 dvd
```

---

### Post by mistypotato on 2007-01-11
Ok....

How do I "UNLINK" it ???

---

