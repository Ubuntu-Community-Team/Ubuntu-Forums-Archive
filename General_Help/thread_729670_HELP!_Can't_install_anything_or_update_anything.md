---
title: "HELP! Can't install anything or update anything"
date: 2008-03-20
forum: General Help
---

### Post by luisjorge on 2008-03-20
Hi everyone! HELP! :(

I followed a guide to get my 80g iPod classic to work properly with amarok ([http://ubuntuforums.org/showthread.php?t=658523](http://ubuntuforums.org/showthread.php?t=658523)), and tried to install gtkpod as well.
My ipod works fine with amarok, but I no longer want gtkpod, so I tried to remove it with synaptic and I can't! I even tried using the terminal, but I got this:

```
luisjorge@ubuntu-inspiron:~$ sudo apt-get purge gtkpod-aac
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gtkpod-aac
0 upgraded, 0 newly installed, 1 to remove and 1096 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 3101kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing gtkpod-aac (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 gtkpod-aac
E: Sub-process /usr/bin/dpkg returned an error code (1)
luisjorge@ubuntu-inspiron:~$ 
```


I tried to reinstall, but I get the same errors. I also tried apt-get autoremove, and happened the same:

```
luisjorge@ubuntu-inspiron:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1096 not upgraded.
2 not fully installed or removed.
Need to get 0B/844kB of archives.
After unpacking 0B of additional disk space will be used.
Selecting previously deselected package gtkpod-aac.
(Reading database ... 161686 files and directories currently installed.)
Preparing to replace gtkpod-aac 0.99.12-1ubuntu1 (using .../gtkpod-aac_0.99.12-1ubuntu1_i386.deb) ...
Unpacking replacement gtkpod-aac ...
The generated cache was invalid.
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
The generated cache was invalid.
dpkg: error processing /var/cache/apt/archives/gtkpod-aac_0.99.12-1ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
The generated cache was invalid.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/gtkpod-aac_0.99.12-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
luisjorge@ubuntu-inspiron:~$ 
```


Now, every time I try to install anything, it gives that error. Also, I can't install any updates, because it says: "Software index is broken. It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."
I can't install anything through synaptic, or any other deb I download.

Does anyone know if I can do something?

Thanks in advance!

Luis Jorge.

---

### Post by wormser on 2008-03-20
Did you try:

```
sudo apt-get install -f
```

---

