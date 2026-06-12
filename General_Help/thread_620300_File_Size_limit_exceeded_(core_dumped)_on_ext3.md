---
title: "File Size limit exceeded (core dumped) on ext3"
date: 2007-11-22
forum: General Help
---

### Post by Polygon on 2007-11-22
im using handbrake to rip a dvd, and the dvd is going over 2 gb but when it hits the 2 gb mark it says

> Encoding: task 2 of 2, 84.05 % (19.94 fps, avg 19.26 fps, ETA 00h35m22s)File size limit exceeded (core dumped)


this is a ext3 drive so 2 gb is NOWHERE near the file size limit

and also, my ulimit output says i can have unlimited file size....

> 
mark@Cactus-Fantastico:~$ ulimit -a
core file size          (blocks, -c) unlimited
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 8191
max locked memory       (kbytes, -l) 32
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 8191
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
mark@Cactus-Fantastico:~$ 


how can i fix this?

---

### Post by jaspreet on 2007-11-22
could there be a limit set  to the size of file handbrake can rip. Maybe somewhere in handbrake's configuration itself.

---

### Post by Polygon on 2007-11-22
its not, a developer for the program is telling me this is a system problem

---

### Post by Polygon on 2007-11-23
bump, this is really annoying and i need to fix this....

---

### Post by Tyche on 2007-11-23
> **Polygon said:**
> bump, this is really annoying and i need to fix this....

I understand how annoying it may be, Polygon89, but there may not be a fix.  I've been Googling for the bug, and am beginning to think that it may be a kernel problem.  Have you submitted a bug report on this?

Tyche (Yea, THAT Tyche)  Hee  hee

---

### Post by mrowth on 2007-11-23
Seem to have the same problem, only with >4 GB files (trying to get OpenSuse 10.3 downloaded here)

ulimit -a gives a different output  (probably due to rt kernel): 


```
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 30
file size               (blocks, -f) unlimited
pending signals                 (-i) 8189
max locked memory       (kbytes, -l) 512000
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 99
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 8189
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
```

Quite the showstoppper...

---

### Post by BoardDWorld on 2007-11-24
Same problem here too at 4GB, "File size limit exceeded (core dumped)" trying to copy an ISO from one partition to another. The funny thing is I wasn't having this problem yesterday???

Edit, problem is it's a Fat32 partition.

---

### Post by mrowth on 2007-11-24
Oh. Right. When I tried it on ext3, I actually only ran out of disk space. When I tried it on FAT32, wget hit the 4GB barrier. I'd downloaded a number of DVD ISOs before, but apparently all of them were <4 GB. 

This doesn't address the problem in the opening post, of course

---

### Post by atlfalcons866 on 2007-11-24
ext3 has problems with large files you should switch to jfs if you have a lot of large files

---

### Post by shad0w_walker on 2007-11-24
> **atlfalcons866 said:**
> ext3 has problems with large files you should switch to jfs if you have a lot of large files

Where exactly are you getting this fact from? I have tons of multi GB files sat around my ext3 file system with out any issues and I have my media centre running ext3 (With slow delete) and the recordings generally end up 2Gb or larger.

---

### Post by Polygon on 2007-11-24
> **atlfalcons866 said:**
> ext3 has problems with large files you should switch to jfs if you have a lot of large files

i have multiple large files around on my ext3 partition that i was trying to rip the dvd to, including a 19 gb file im looking at right now. Ext3 can handle file sizes up to 2 terabytes i think.


so... why is linux making the program dump core for a 2 gb file when its no where NEAR the limit of the filesystem?

---

### Post by atlfalcons866 on 2007-11-25
mythtv says jfs is the fastest file system for larger files

---

### Post by Stygmata on 2007-11-25
I'm getting the same behavior using k9copy and also dvdbackup - miy system's an upgrade from Feisty, PPC version (Mac hardware).  

Off to see if a bug's been posted.

---

### Post by Polygon on 2007-11-27
> **atlfalcons866 said:**
> mythtv says jfs is the fastest file system for larger files

might be the fastest, but ext3 can certainly handle large files....

---

### Post by callan79 on 2007-11-27
> **Polygon said:**
> so... why is linux making the program dump core for a 2 gb file when its no where NEAR the limit of the filesystem?

Hi Guys,

I'm clutching at straws here, but I just want to make sure the ext3 filesystem is a LOCAL device, and not a network drive?

I, too, have many >10GB files on my ext3 device.

But I know that samba (network file sharing) has an issue with >2GB.

Cheers
Callan

---

### Post by Stygmata on 2007-11-27
Yes in my case.  Local hard drive, ext3, k9copy starts ripping, crashes with "file size exceeded, core dumped" at 2GB. 

I've verified if I use mencode manually, this doesn't happen.

---

### Post by Polygon on 2007-11-28
[http://handbrake.m0k.org/forum/viewtopic.php?t=3597](http://handbrake.m0k.org/forum/viewtopic.php?t=3597)

that is the thread on the handbrake forums about this, if you look there, me and another guy did a test with dd to see if we could create 2+gb files, and we could.

and ulimit also says that we have unlimited file sizes

its a local drive (a usb external drive) so samba isnt a issue

---

