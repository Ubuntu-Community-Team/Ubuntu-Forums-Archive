---
title: "RTMPDump - Segmentation Fault After Compile"
date: 2012-12-10
forum: General Help
---

### Post by Kr0nZ on 2012-12-10
I already have rtmpdump installed from apt-get, but that version of rtmpdump doesn't seem to work properly, rtmpsrv works fine.

So I tried compiling the newest version from
"git://git.ffmpeg.org/rtmpdump"

After I run make
```
make VERSION="2.4.$(git log --pretty=format:'%h' -n 1)~git"
```

I then try testing it with
```
./rtmpdump
```

But I just get a segmentation fault such as
```
RTMPDump 2.4.19d3636~git
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Segmentation fault (core dumped)
```


What am I doing wrong?

I'm running Ubuntu 12.04
```
uname -a
Linux myth-htpc 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686 i686 i386 GNU/Linux
```

```
lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:        12.04
Codename:       precise
```

---

### Post by andrew.46 on 2012-12-11
I am not on my Ubuntu partition at the moment but I have successfully compiled and used this version of rtmpdump:

[http://ponce.cc/slackware/sources/repo/rtmpdump-20120308_7340f6d.tar.xz](http://ponce.cc/slackware/sources/repo/rtmpdump-20120308_7340f6d.tar.xz)

Perhaps see if you have more luck with this one?

---

