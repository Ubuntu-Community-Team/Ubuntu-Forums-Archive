---
title: "Looking for command-line dvd-burning backup tool"
date: 2008-05-16
forum: General Help
---

### Post by unutbu on 2008-05-16
I decided to back up /etc and /var onto a DVD today:

I set up a directory like this:
```
  /home/cyrano/backup-var-etc:
  total used in directory 24 available 263630376
  drwxr-xr-x   2 cyrano cyrano  4096 2008-05-16 10:53 .
  drwxr-xr-x 111 cyrano cyrano 20480 2008-05-16 11:50 ..
  lrwxrwxrwx   1 cyrano cyrano     4 2008-03-01 11:19 etc -> /etc
  lrwxrwxrwx   1 cyrano cyrano     4 2008-05-16 09:56 var -> /var
```

```

11:30:03 cyrano@farmer:~% sudo growisofs -joliet-long -Z /dev/scd0 -R -J -V "2008-05-16-dvd5" -f /home/cyrano/backup-var-etc
11:34:21 cyrano@farmer:~% mount /media/cdrom

```

I was surprised to find that the DVD now contains:

```
  /media/cdrom/var/lib:
  total used in directory 257 available 0
  drwxr-xr-x 11 root root   4096 2007-10-15 19:19 .
  drwxr-xr-x 15 root root   2048 2007-10-15 19:31 ..
  drwxr-xr-x  2 root root   4096 2007-10-15 19:17 compat
  -rw-r--r--  1 root root    974 2007-09-30 12:02 compat.dir
  drwxr-xr-x  2 root root   2048 2008-05-16 06:56 compiled
  drwxr-xr-x  4 root root   4096 2007-10-15 19:17 geometry
  -rw-r--r--  1 root root   3028 2007-09-30 12:02 geometry.dir
  drwxr-xr-x  4 root root   4096 2007-10-15 19:17 keycodes
  -rw-r--r--  1 root root   3019 2007-09-30 12:02 keycodes.dir
  drwxr-xr-x  5 root root   2048 2007-10-15 19:17 keymap
  -rw-r--r--  1 root root  14662 2007-09-30 12:02 keymap.dir
  drwxr-xr-x  2 root root   2048 2007-10-15 19:17 rules
  drwxr-xr-x  2 root root   2048 2007-10-15 19:17 semantics
  -rw-r--r--  1 root root    134 2007-09-30 12:02 semantics.dir
  drwxr-xr-x 11 root root  12288 2007-10-15 19:17 symbols
  -rw-r--r--  1 root root  23740 2007-09-30 12:02 symbols.dir
  drwxr-xr-x  2 root root   2048 2007-10-15 19:17 types
  -rw-r--r--  1 root root    624 2007-09-30 12:02 types.dir
  -rwxr-xr-x  1 root root 173784 2006-08-04 10:00 xkbcomp
```

But this is all wrong! The directory growisofs saved as /var/lib is actually /etc/X11/xkb. 

I realize that growisofs gives this warning
```
Warning: -follow-links does not always work correctly; be careful.
```
but I didn't realize just how broken the '-f' flag could be. 

So, if we can't use symlinks, what is the proper way to backup /etc and /var onto 1 DVD using CLI tools?
I would prefer a method that does not require copying everything I want to back up into a temporary directory, but I'm open to all suggestions.

By the way, /etc contains symlinks, so even if I had not set up my ~/backup-var-etc directory the way I had, I still do not know if I can trust growisofs.

---

### Post by logos34 on 2008-05-16
> **unutbu said:**
> 
So, if we can't use symlinks, what is the proper way to backup /etc and /var onto 1 DVD using CLI tools?
I would prefer a method that does not require copying everything I want to back up into a temporary directory, but I'm open to all suggestions.

maybe I'm misunderstanding your question, but I just backed up /var (directly) using your command and it worked fine:

sudo growisofs -joliet-long -Z /dev/dvd -R -J -V "2008-05-16-dvd5" -f /var

EDIT: if you create a .tar.gz first it will follow symlinks.  Of course it adds another step (still have to burn it) but has the virtue of compressing it smaller

---

### Post by unutbu on 2008-05-16
Hi logos34, thanks for the response.

I just tried
```
sudo growisofs -joliet-long -Z /dev/dvd -R -J -V "2008-05-16-dvd5" -f /var /etc
```

and yes, the strange bug did not exhibit itself here. Assuming the backup is a faithful copy, I just have one other problem now:

The above command puts the contents of both /etc/* and /var/* all together under /media/cdrom.

How can I save both on one DVD and yet keep the /var and /etc directories separate?

PS. Thanks for your suggestion about tar. I decided to go with "fat-and-lazy" backup without tar/bzip2 because in the past I've sometimes found a need to just restore a single file and it was rather slow having to download a 700MB (CD) tar.bz2 file just to restore the single file. Now that I'm starting to use DVDs, I'm even more reticent.

---

### Post by unutbu on 2008-05-16
If anyone is willing to try:
```
cd
mkdir backup
ln -s /etc backup/etc
ln -s /var backup/var
sudo growisofs -joliet-long -Z /dev/scd0 -R -J -V "2008-05-16-dvd5" -f backup

```

I'd be much obliged to hear if the growisofs "bug" can be reproduced.

---

### Post by logos34 on 2008-05-16
> **unutbu said:**
> How can I save both on one DVD and yet keep the /var and /etc directories separate?

Good question.  maybe someone else knows.

---

### Post by unutbu on 2008-05-16
I made a mistake when I said this was a bug in growisofs. It appears the bug is really in genisoimage, which growisofs calls.

You can see the bug for yourself (I think) without having to burn a CD, as long as you have some disk space:
```

cd
mkdir backup
ln -s /etc backup/etc
ln -s /var backup/var
sudo genisoimage -R -f -o /tmp/dvdimage backup
sudo mkdir /media/dvd
sudo mount /tmp/dvdimage -r -t iso9660 -o loop /media/dvd
```

You'll see that /media/dvd/var/lib is not the same as /var/lib -- if your system is like mine, the contents will look more like /etc/X11/xkb.

---

