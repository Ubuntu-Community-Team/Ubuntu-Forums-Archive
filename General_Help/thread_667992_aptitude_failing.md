---
title: "aptitude failing"
date: 2008-01-14
forum: General Help
---

### Post by bkline on 2008-01-14
Update Manager, which has been working fine up until today, started failing with the following error message:

(Reading database ... dpkg: error processing /var/cache/apt/archives/libedataserver1.2-9_1.12.1-0ubuntu2_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `cvs': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libedataserver1.2-9_1.12.1-0ubuntu2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

I tried running aptitude from the command line, but get the same result.

Does anyone know what this error message means, and how to correct the problem?

Thanks!

Bob Kline

---

### Post by sumguy231 on 2008-01-15
Try from a terminal:
```
sudo dpkg --configure -a
```

---

### Post by bkline on 2008-01-15
> Try from a terminal ...

Thanks for the tip, but dpkg didn't produce any output, even with -D cranked all the way up, and aptitude still failed with the same error message.  Any other thoughts?

Bob

---

### Post by bkline on 2008-01-15
I just got this message from apticron:

/etc/cron.daily/apticron:
Failed to fetch [http://ftp.debian.org/debian/dists/etch/Release.gpg](http://ftp.debian.org/debian/dists/etch/Release.gpg)  Could not connect to ftp.debian.org:80 (128.101.240.212), connection timed out
E: Some index files failed to download, they have been ignored, or old ones used instead.

Could this be related to the aptitude failures?

Bob

---

### Post by bkline on 2008-01-15
It appears that /var/lib/dpkg/info/cvs.list is unreadable.  I'll do an fsck tonight when I have physical access to the system.  Sorry about the message about apticron - I hadn't had my coffee yet, and didn't notice that it was from a different machine (and not even an Ubuntu machine at that). :(

Any advice about how to make the package manager happy again if I can't recover cvs.list?

Bob

---

### Post by bkline on 2008-01-15
I wasn't able to recover cvs.list using fsck.  Any tips on how to go about reconstructing that file?

---

