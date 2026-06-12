---
title: "Problems building Lemonbar from source on Ubuntu 14.04 system"
date: 2016-01-11
forum: General Help
---

### Post by globetrotterdk on 2016-01-11
I am experiencing a problem building lemonbar from source, to use with bspwm. I cloned the git

```
~/Downloads$ git clone https://github.com/LemonBoy/bar.git
Cloning into 'bar'...
remote: Counting objects: 601, done.
remote: Total 601 (delta 0), reused 0 (delta 0), pack-reused 601
Receiving objects: 100% (601/601), 220.35 KiB | 0 bytes/s, done.
Resolving deltas: 100% (330/330), done.
Checking connectivity... done.
```
Everything looks OK
```
~/Downloads/bar$ make
cc -Wall -std=c99 -Os -DVERSION="\"6198527\"" -o lemonbar.o -c lemonbar.c
lemonbar.c: In function ‘main’:
lemonbar.c:1341:42: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result [-Wunused-result]
                                     write(STDOUT_FILENO, area->cmd, strlen(area->cmd));
                                          ^
lemonbar.c:1342:42: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result [-Wunused-result]
                                     write(STDOUT_FILENO, "\n", 1);
                                          ^
cc -o lemonbar lemonbar.o -lxcb -lxcb-xinerama -lxcb-randr
```

I have checked to see if my system has the latest versions of libxcb-xinerama0-dev and libxcb-randr0-dev which I do, so I don't understand the error being kicked up. I don't have much experiencing compiling from source, so I could really use some help...

---

### Post by sandyd on 2016-01-11
You can safely ignore those, they are only warnings.

Are there any issues with the binary produced with the compiling?

---

### Post by globetrotterdk on 2016-01-11
Great. No problems. I ran sudo checkinstall to create packages for all of the bspwm bits, so that I can install them on another computer - a computer with a minimal Ubuntu 14.04 install. Thanks for the quick reply.

---

