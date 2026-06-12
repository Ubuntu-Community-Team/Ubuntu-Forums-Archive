---
title: "3rd party printer drivers package has corrupted package management system"
date: 2007-03-07
forum: General Help
---

### Post by Josh M on 2007-03-07
I downloaded and installed a debian package containing printer drivers from the Brother website. Bad idea. The package did not install completely, and now I get an error whenever I try to do anything involving the package manager. 

Here is me trying to remove the offending package with dpkg.

> josh@josh-desktop:~/temp$ sudo dpkg --remove hl1440lpr
(Reading database ... 80650 files and directories currently installed.)
Removing hl1440lpr ...
/var/lib/dpkg/info/hl1440lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing hl1440lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl1440lpr

(I get this error anytime I try to use apt-get, synaptic, etc.)

I checked /etc/init.d and indeed there is no file or directory called lpd. 

Any ideas?

Thanks in advance!

---

### Post by saphil on 2007-03-08
You are like me, then.  I love to try stuff that nobody else has tried.  I have blown up more OSes...  maybe 30 or 40 OSes.

I had a similar issue based on having some beowulf-cluster packages that were corrupted.  I tried a couple of things and eventually got it cleared out: 

```
root@yossarian:/home/wolf# apt-get clean

```
 and
```
root@yossarian:/home/wolf# apt-get autoclean

```

Autoclean gets rid of old packages
Clean gets rid of all packages

This might not work, you might need to go into the file system and get rid of the history or db file, but that is risky.

What version of Ubuntu are you using?

---

