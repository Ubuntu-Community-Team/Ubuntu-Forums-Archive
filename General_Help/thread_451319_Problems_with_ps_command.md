---
title: "Problems with ps command"
date: 2007-05-22
forum: General Help
---

### Post by brodiwan on 2007-05-22
Hi, I have had ubuntu 'dapper' on a couple of servers now for some time and everything was working just fine. Now on one of my servers running 'Merak' email server I get this strange output when I do a ps -ef command.

root@eserver:~# ps -ef
  PID   TTY   STAT  TIME COMMAND
 4439   1     S    0:00 /sbin/getty 38400 tty1 HOME=/ DPKG_ARCH=i386 PROGRESS_S
 4440   2     S    0:00 /sbin/getty 38400 tty2 HOME=/ DPKG_ARCH=i386 PROGRESS_S
 4441   3     S    0:00 /sbin/getty 38400 tty3 HOME=/ DPKG_ARCH=i386 PROGRESS_S
 4442   4     S    0:00 /sbin/getty 38400 tty4 HOME=/ DPKG_ARCH=i386 PROGRESS_S
 4443   5     S    0:00 /sbin/getty 38400 tty5 HOME=/ DPKG_ARCH=i386 PROGRESS_S
 4446   6     S    0:00 /sbin/getty 38400 tty6 HOME=/ DPKG_ARCH=i386 PROGRESS_S
15545  ?      S    0:00 -bash USER=root LOGNAME=root HOME=/root PATH=/usr/local
15587  ?      R    0:00  \_ ps -ef TERM=xterm SHELL=/bin/bash SSH_CLIENT=152.11

As you can see I cant see any of the other proccesses (which are running fine). Also when I now do an ls -als I get this message :

root@eserver:~# ls -als
ls: unrecognized prefix: do
ls: unparsable value for LS_COLORS environment variable
total 32256
    4 drwxr-xr-x   6 root     root         4096 Apr 19 16:22 .
    4 drwxr-xr-x  23 root     root         4096 Apr 19 16:22 ..
    4 drwx------   2 root     root         4096 Nov 14  2006 .aptitude

Same if I try and run 'top' to see running processes. Any ideas ?????. I want to avoid reloading all the software because up until now I have had no issues with ubuntu, indeed its still running my email application ok.   HELP !!!!

---

### Post by aysiu on 2007-05-22
This may help you with the second problem:
[http://www.linuxsa.org.au/pipermail/linuxsa/2006-April/083533.html](http://www.linuxsa.org.au/pipermail/linuxsa/2006-April/083533.html)

---

