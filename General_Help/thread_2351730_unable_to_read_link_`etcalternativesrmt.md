---
title: "unable to read link `/etc/alternatives/rmt"
date: 2017-02-06
forum: General Help
---

### Post by zensys on 2017-02-06
After sudo dpkg --configure -a (I had an issue with updating Trusty) I get:

```
update-alternatives: error: unable to read link `/etc/alternatives/rmt': Invalid argument
dpkg: error processing package tar (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 tar
```

I cannot find a way to solve this nowhere. Any suggestions?

---

### Post by steeldriver on 2017-02-06
What do

```

ls -l /etc/alternatives/rmt

update-alternatives --query rmt

```

say?

---

### Post by zensys on 2017-02-08
```
-rwxr-xr-x 1 root root 52136 feb  4  2014 /etc/alternatives/rmt*
```

```
Name: rmt
Link: /usr/sbin/rmt
Slaves:
 rmt.8.gz /usr/share/man/man8/rmt.8.gz
Status: auto
update-alternatives: error: unable to read link `/etc/alternatives/rmt': Invalid argument

```

---

### Post by steeldriver on 2017-02-08
Hmm... so it seems that somehow your /etc/alternatives/rmt has become a real file instead of a symlink

What is the output of

```

ls -l /usr/sbin/rmt*

```

---

### Post by zensys on 2017-02-13
```
~$ ls -l /usr/sbin/rmt*
lrwxrwxrwx 1 root root    21 sep  6  2014 /usr/sbin/rmt -> /etc/alternatives/rmt*
-rwxr-xr-x 1 root root 52136 nov 17 17:40 /usr/sbin/rmt-tar*
```

---

### Post by Bashing-om on 2017-02-13
zensys; Hello;

Looks to me that your symlinks are in error ( can only point to a single target )
My outputs:
> 
sysop@x1604:~$ ls -l /usr/sbin/rmt*
lrwxrwxrwx 1 root root    21 Oct 16 22:42 /usr/sbin/rmt -> /etc/alternatives/rmt
-rwxr-xr-x 1 root root 56264 Nov 17 10:40 /usr/sbin/rmt-tar
sysop@x1604:~$ 

sysop@x1604:~$ ls -l /etc/alternatives/rmt
lrwxrwxrwx 1 root root 17 Oct 16 22:36 /etc/alternatives/rmt -> /usr/sbin/rmt-tar

sysop@x1604:~$ ls -l /usr/sbin/rmt-tar
-rwxr-xr-x 1 root root 56264 Nov 17 10:40 /usr/sbin/rmt-tar
sysop@x1604:~$ 


[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by steeldriver on 2017-02-13
@Bashing-om I believe the asterisks in the OP's output are because they have `ls` aliased to `ls -F` (so * == executable)

The issue seems to be that their /etc/alternatives/rmt-tar is an actual executable, rather than a symlink (and presumably the installer is balking at overwriting it)

Based on file size, it's probably a copy of /usr/sbin/rmt-tar

Probably the way I would go about this is to rename that file (in case it turns out to have been something other than a misplaced copy)

```

sudo mv /etc/alternatives/rmt-tar /etc/alternatives/rmt-tar.old

```

and then try again. It *may *be necessary to fix update-alternatives manually - but let's assume for now it's smart enough to fix itself once the file is out of the way.

---

