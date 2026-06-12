---
title: "broken dependency help"
date: 2007-04-01
forum: General Help
---

### Post by acejones on 2007-04-01
```
mike@ace-nix:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  beryl-plugins-unsupported
The following NEW packages will be installed:
  beryl-plugins-unsupported
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B/81.2kB of archives.
After unpacking 270kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 142520 files and directories currently installed.)
Unpacking beryl-plugins-unsupported (from .../beryl-plugins-unsupported_0.2.0~0beryl1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/beryl-plugins-unsupported_0.2.0~0beryl1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/beryl/libgroup.so', which is also in package beryl-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/beryl-plugins-unsupported_0.2.0~0beryl1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Can someone help me resolve this?

---

### Post by neoaddict on 2007-04-01
You gotta choose one or the other, as it seems you can't have both of them at the same time.  :-/

---

### Post by acejones on 2007-04-01
ok.... so how do I resolve the problem?

---

### Post by neoaddict on 2007-04-01
Oo, here goes:

1) Add this to your /etc/apt/sources.list file:

```
[FONT=courier new,courier]# Daily Updated Beryl (and related projects) Packages&#8230;
deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
deb-src http://download.tuxfamily.org/3v1deb edgy beryl-svn
```

2) Run this command:

```
[/FONT]wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

3) Run this command:

```
sudo apt-get update && sudo apt-get install beryl-plugins-unsupported
```

Trevino's Beryl repository is the cutting edge of Beryl, so be warned that your Beryl might break.

---

### Post by acejones on 2007-04-01
Thanks a ton, that got me back up and going.  I did lose all the other beryl options, but I think I look around for that.

[IMG]http://acejones.net/Beryl%20Settings%20Manager.jpg[/IMG]

---

### Post by neoaddict on 2007-04-01
^ Odd.

Have you tried reinstalling Beryl?

Beryl's settings windows still looks normal for me (I've been using that repo for months).

If re-installing doesn't fix it, remove the directory .beryl in your home folder.

---

