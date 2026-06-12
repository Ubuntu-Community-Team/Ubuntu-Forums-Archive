---
title: "crontab permissions problems??"
date: 2007-11-27
forum: General Help
---

### Post by el_baby on 2007-11-27
Hi there,

I have a quite plain gutsy installation and I just noticed I can't create/edit my crontab...

crontab -e

yelds: 
crontabs/baby: Permission denied

I can sudo and edit things by hand, but I don't want to...

I connected to a gutsy server I've installed and it works OK...

Here's how permissions are set in the cron tree:
```

$ sudo find /var/spool/cron -ls
 50136    0 drwxr-xr-x   5 daemon   daemon        120 Oct 25 09:20 /var/spool/cron
 50138    0 drwxrwx--T   2 daemon   daemon         72 Oct 25 09:22 /var/spool/cron/atjobs
100047    4 -rw-------   1 daemon   daemon          2 Oct 25 09:22 /var/spool/cron/atjobs/.SEQ
 50137    0 drwxrwx--T   2 daemon   daemon         48 Feb 20  2007 /var/spool/cron/atspool
 50397    0 drwx-wx--T   2 root     crontab        96 Nov 27 20:06 /var/spool/cron/crontabs
   141    0 -rw-------   1 baby     crontab         0 Nov 27 20:06 /var/spool/cron/crontabs/baby
   115    4 -rw-------   1 root     root          201 Nov 27 20:00 /var/spool/cron/crontabs/root

```

The "baby" empty cron in there I created it via sudo touch/chown/chmod

Any help very appreciated...

---

### Post by el_baby on 2007-11-30
BUMP

any takers?

---

### Post by brolin on 2007-12-06
Have you compared the permissions of the /var/spool/cron/ tree between your server and system where you cannot create nor edit your crontab?

Have you checked that your user account belongs to the same groups on both systems?

I have a Debian (not Ubuntu) system where the permissions and ownership of directories under /var/spool/cron/ used by at(1) had been lost and were consequently incorrect.  at(1) did not have permission to create a new job file.  I Googled for "/var/spool/cron/atjobs/ debian" and found this post.  I fixed my at(1) problem by changing the ownership and mode of my directories under /var/spool/cron/ to match yours.  Thanks. :)

---

### Post by el_baby on 2007-12-07
Well... it turned out to be a permissions problem on the crontab *command*... the files and directories themselves were just right, but /usr/bin/crontab needed the setgid bit and didn't have it.

Now it seems to work fine. FTR, it was (wrong):
**-rwxr-xr-x 1 root crontab 26832 2006-12-20 11:46 /usr/bin/crontab***
and now its (correct):
**-rwxr-sr-x 1 root crontab 26832 2006-12-20 11:46 /usr/bin/crontab***

The command to solve this was:
**```
$ sudo chmod g+s /usr/bin/crontab
```**

---

### Post by brolin on 2007-12-07
Interesting.  I did not even know the crontab executable was setgid! :)

---

