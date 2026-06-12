---
title: "WARNING: Hard link ..."
date: 2006-11-11
forum: General Help
---

### Post by supahfly on 2006-11-11
Hi all,

This is not the first time I see this error :
WARNING: Hard link count is wrong for /proc/6230: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.

This yields in to an incorrect search:
I just installed apache, and when I do :
```
sudo find / -name apache
```
it gives the error and returns no results ...

This is what is in my proc/6230 folder:

ls -la
total 0
dr-xr-xr-x   5 kevain kevain 0 2006-11-11 10:43 .
dr-xr-xr-x 120 root   root   0 2006-11-11 10:08 ..
dr-xr-xr-x   2 kevain kevain 0 2006-11-11 12:58 attr
-r--------   1 kevain kevain 0 2006-11-11 13:02 auxv
-r--r--r--   1 kevain kevain 0 2006-11-11 13:02 cmdline
-r--r--r--   1 kevain kevain 0 2006-11-11 13:02 cpuset
lrwxrwxrwx   1 kevain kevain 0 2006-11-11 13:02 cwd -> /home/kevain/.azureus
-r--------   1 kevain kevain 0 2006-11-11 13:02 environ
lrwxrwxrwx   1 kevain kevain 0 2006-11-11 13:02 exe -> /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/bin/java
dr-x------   2 kevain kevain 0 2006-11-11 12:58 fd
-r--r--r--   1 kevain kevain 0 2006-11-11 13:02 maps
-rw-------   1 kevain kevain 0 2006-11-11 13:02 mem
-r--r--r--   1 kevain kevain 0 2006-11-11 13:02 mounts
-r--------   1 kevain kevain 0 2006-11-11 13:02 mountstats
-rw-r--r--   1 kevain kevain 0 2006-11-11 13:02 oom_adj
-r--r--r--   1 kevain kevain 0 2006-11-11 13:02 oom_score
lrwxrwxrwx   1 kevain kevain 0 2006-11-11 13:02 root -> /
-rw-------   1 kevain kevain 0 2006-11-11 13:02 seccomp
-r--r--r--   1 kevain kevain 0 2006-11-11 13:02 smaps
-r--r--r--   1 kevain kevain 0 2006-11-11 13:02 stat
-r--r--r--   1 kevain kevain 0 2006-11-11 13:02 statm
-r--r--r--   1 kevain kevain 0 2006-11-11 13:02 status
dr-xr-xr-x  64 kevain kevain 0 2006-11-11 12:58 task
-r--r--r--   1 kevain kevain 0 2006-11-11 13:02 wchan


Some help anyone ?
Please be not too technical, I am just a linux lover, no fanatic :-)

---

### Post by vitko on 2007-08-20
See [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=402999](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=402999)

---

