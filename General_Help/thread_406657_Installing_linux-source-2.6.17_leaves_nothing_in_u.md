---
title: "Installing linux-source-2.6.17 leaves nothing in /usr/src"
date: 2007-04-11
forum: General Help
---

### Post by nmsmith on 2007-04-11
I am trying to get a remote working with lirc. It seems I need the linux source package installed, which I have successfully done before on dapper and breezy machines.

On this edgy machine all I get is:

```
root@cloanthus:/usr/src# apt-get install linux-source-2.6.17 build-essential gcc-3.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-source-2.6.17 is already the newest version.
build-essential is already the newest version.
gcc-3.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

but

```
root@cloanthus:/usr/src# ls -l
total 596
drwxrwxrwx 8 nick users   4096 2006-10-14 07:27 lirc-0.8.1pre2
-rw-r--r-- 1 root src   601864 2006-10-14 07:41 lirc-0.8.1pre2.tar.bz2
```

Why doesn't the source file appear? A locate search for "linux-source" reveals (among others) the following file: */var/lib/dpkg/info/linux-source-2.6.17.list*

And that file lists* /usr/src/linux-source-2.6.17.tar.bz2* as an installed file. But I can't see it.

What's going on?

---

### Post by nmsmith on 2007-04-11
SOLVED.

I don't know why, but remove and install fixed it.

---

