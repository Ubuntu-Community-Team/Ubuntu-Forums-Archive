---
title: "[SOLVED] Can anyone help me aMule says too many open files error.."
date: 2007-12-12
forum: General Help
---

### Post by hopelessone on 2007-12-12
Hi,

is this error a aMule or a linux one?

2007-12-12 16:57:57: PartFile.cpp(885): ERROR while saving partfile: Failed to open part.met file (001.part.met ==> Movie.avi)
2007-12-12 16:57:58: ClientCreditsList.cpp(360): Credits: Error while creating signature: OS_Rng: open /dev/urandom operation failed with error 24

my:

box@fbox-desktop:~$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 6140
max locked memory       (kbytes, -l) 32
max memory size         (kbytes, -m) unlimited
[COLOR="Red"]open files                      (-n) 1024[/COLOR]
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 6140
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

is linux like windows? do i have to increase the open files? because i did in aMule increase from 400 max connections when i had this error and even tried 5000 max connections nothing works...

what can i do guys?

many thanks...!!

---

### Post by hopelessone on 2007-12-12
Fix:

edit /etc/security/limits.conf

and add :
[username] soft nofile 4096
[username] hard nofile 4096

hope that helps others...

cheers...

happy aMuling...

---

