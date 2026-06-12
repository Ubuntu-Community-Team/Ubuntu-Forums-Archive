---
title: "/boot is full...and removing old images..."
date: 2013-05-02
forum: General Help
---

### Post by LumbeeNDN on 2013-05-02
Ubuntu Sever 12.04

Hey folks, I have a server that I noticed /boot partition was filling up. I followed recommendations from this post...

[http://ubuntuforums.org/showthread.php?t=1435818](http://ubuntuforums.org/showthread.php?t=1435818)

..that worked great. My only question is after executing commands to remove a few images like...

sudo apt-get remove linux-image-3.2.0-39-gen

...when I list the images with sudo dpkg --list 'linux-image*', the packages I removed still show up in this list, even though I can see the disk space has been freed up. What am I missing?

---

### Post by kalehrl on 2013-05-02
You're not missing anything.
```
root@eeepc:/home/kalehrl# dpkg -l | grep linux-image-
[COLOR=#ff0000]rc  [/COLOR]linux-image-3.2.0-33-generic      3.2.0-33.52                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
[COLOR=#ff0000]rc  [/COLOR]linux-image-3.2.0-34-generic      3.2.0-34.53                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
[COLOR=#ff0000]rc  [/COLOR]linux-image-3.2.0-35-generic      3.2.0-35.55                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
[COLOR=#ff0000]rc  [/COLOR]linux-image-3.2.0-36-generic      3.2.0-36.57                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
[COLOR=#ff0000]rc  [/COLOR]linux-image-3.2.0-38-generic      3.2.0-38.61                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
[COLOR=#ff0000]rc  [/COLOR]linux-image-3.2.0-39-generic      3.2.0-39.62                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-40-generic      3.2.0-40.64                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic               3.2.0.40.48                             Generic Linux kernel image
```
Removed kernels are marked with [COLOR=#ff0000]rc[/COLOR].

---

### Post by LumbeeNDN on 2013-05-02
Ahh...you are correct sir! Why is that? Why are they kept hanging around?

---

### Post by prodigy_ on 2013-05-02
One-liner to purge all old kernels: [http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

---

### Post by Impavidus on 2013-05-02
rc stands for remaining configuration. They can be completely removed by using sudo apt-get purge ...

---

