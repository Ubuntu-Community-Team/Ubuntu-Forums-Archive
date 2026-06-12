---
title: "Unable to login. help Please"
date: 2008-05-26
forum: General Help
---

### Post by Ohwii on 2008-05-26
Hi guys,

well, after I updated the system with the new fglx... etc. I am unable to log in into ubuntu. 

After I login I can see my desktop and everything very nicely, but after 1 or 2 seconds. the whole desktop goes white. I guess underneath the white screen everything is still working, since I can rotate the cube( eventhough it is very slow) and i can run programms in gnome-do. Since I can see the window-switcher (alt+tab)without the logos. 

i assume it has something to do with the script i am using or it is something with the ATI drivers,again. 

Please, I really need help. otherwise I just have to go back to my windows XP:(, because now is the 3rd time that I have issues with hardy heron.

Cheers 

Ohwii

PS the script i am using 

```
#!/bin/bash
sleep 5
compiz &
while [ -z $(ps -o comm= -C compiz.real) ]; do
  sleep 2
done
avant-window-navigator &
```

---

### Post by teaker1s on 2008-05-26
it is compriz window manager and can be solved by 
[http://ubuntuforums.org/showthread.php?t=807048&highlight=white+screen]("http://ubuntuforums.org/showthread.php?t=807048&highlight=white+screen")
I had similar issues and completely removed compriz, installed ati binary driver. and then reinstall compiz

---

### Post by Ohwii on 2008-05-26
props to the man from england!!

 I will give it a shot. Thank you, Sir

---

### Post by Ohwii on 2008-05-26
could someone help with the binary installation please this is what i get when I want to install the packages


 sudo sh ati-driver-installer-8-5-x86.x86_64.run --buildpkg Ubuntu/8.04

```
 * Starting atieventsd                                                          /usr/sbin/atieventsd: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
                                                                         [fail]

Setting up fglrx-kernel-source (2:8.493.1-0ubuntu1) ...
Adding Module to DKMS build system

Error! DKMS tree already contains: fglrx-8.493.1
You cannot add the same module/version combo more than once.
Doing initial module build

Error! This module/version has already been built on: 2.6.24-17-generic
Directory: /var/lib/dkms/fglrx/8.493.1/2.6.24-17-generic/i686
already exists.  Use the dkms remove function before trying to build again.
Installing initial module

Error! This module/version combo is already installed
for kernel: 2.6.24-17-generic (i686)
Done.

Errors were encountered while processing:
 fglrx-amdcccle_8.493.1-0ubuntu1_i386.deb

```

---

### Post by teaker1s on 2008-05-26
can you get a gui as I'd recommend envy installer script. failing that can you provide the link you used to install the drivers and I can suggest how to remove

---

### Post by Ohwii on 2008-05-26
Oh yes.

please forgive.

 I forgot the link.

 I used this guide [Guide ATI ]("http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide") to install the drivers. 

Thank you for your time I really appreciate it.

Talk to you soon 

Ohwii

---

### Post by teaker1s on 2008-05-26
By the looks of it the installer creates deb packages for ubuntu. you don't say if you have gui or not. 
If you have gui then I really would recommend envy to remove and reinstall your graphics.
 if you have gui 
```
gksudo synaptic
``` 

Otherwise we could 
sudo apt-get remove xorg-driver-fglrx fglrx-kernel-source fglrx-amdcccle

after you have done this you will need to un blacklist anything you have blacklisted now you won't have gedit if your stuck in console use "nano"

---

