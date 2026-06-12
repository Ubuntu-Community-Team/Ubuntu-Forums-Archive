---
title: "xe emulator"
date: 2006-11-20
forum: General Help
---

### Post by TheRingmaster on 2006-11-20
could someone help me install XE emulator. I have downloaded the the file and extracted it all on the desktop. here is what the readme file says.      


>                                                   *Requirements*

GTK+2.0 or above is required. Since GTK+ could be configured differently on
different systems, you will need to link Xe manually. 

------------------------------------------------------------------------

*Simple Install*

Install to system directory:

   1. login as root
   2. 'make' to link the software
   3. 'make install' will install it to the system directory 

*Manual Install*

Install to system directory:

   1. login as root
   2. 'make' to link the software
   3. 'mkdir /usr/local/lib/xe' to create system directory
   4. 'mv xe rc manual modules /usr/local/lib/xe' to move files to
      system directory
   5. 'ln -sf /usr/local/lib/xe/xe /usr/local/bin/xe' to link binary into
      system path 

Install to user directory:

   1. 'make' to link the software
   2. 'mkdir ~/.xe' to create local directory
   3. 'mv xe rc manual modules ~/.xe' to move file to local directory
   4. link or move ~/.xe/xe' to your local bin directory 

------------------------------------------------------------------------

For more information please read the user's manual at:

[http://www.xe-emulator.com/](http://www.xe-emulator.com/)[]("http://www.xe-emulator.com/")

---

### Post by grte on 2006-11-20
> **TheRingmaster said:**
> could someone help me install XE emulator. I have downloaded the the file and extracted it all on the desktop. here is what the readme file says.      


[]("http://www.xe-emulator.com/")

Try opening a terminal and typing the following:

```
cd <extraction directory>
sudo make
sudo make install
```

---

### Post by TheRingmaster on 2006-11-20
> **grte said:**
> Try opening a terminal and typing the following:

```
cd <extraction directory>
sudo make
sudo make install
```

had some problems, see screenshot

---

### Post by grte on 2006-11-21
Try the command ```
sudo apt-get install build-essential libgtk2.0-dev
``` then try the original instructions again.

---

### Post by TheRingmaster on 2006-11-21
> petey@Data:~$ sudo apt-get install build-essential libgtk2.0-dev
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  mplayer-skins libmp4v2-0 libtext-glob-perl libendeavour2-2 libdate-calc-perl
  libcarp-clan-perl libfile-find-rule-perl libnumber-compare-perl
  libbit-vector-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libatk1.0-dev libcairo2-dev libexpat1-dev libfontconfig1-dev
  libfreetype6-dev libglib2.0-dev libice-dev libpango1.0-dev libpng12-dev
  libsm-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxrandr-dev
  libxrender-dev x11proto-core-dev x11proto-fixes-dev x11proto-input-dev
  x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev xtrans-dev zlib1g-dev
Suggested packages:
  libcairo2-doc libglib2.0-doc libgtk2.0-doc libpango1.0-doc
The following NEW packages will be installed:
  libatk1.0-dev libcairo2-dev libexpat1-dev libfontconfig1-dev
  libfreetype6-dev libglib2.0-dev libgtk2.0-dev libice-dev libpango1.0-dev
  libpng12-dev libsm-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxrandr-dev
  libxrender-dev x11proto-core-dev x11proto-fixes-dev x11proto-input-dev
  x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev xtrans-dev zlib1g-dev
0 upgraded, 32 newly installed, 0 to remove and 0 not upgraded.
Need to get 7434kB of archives.
After unpacking 28.3MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
petey@Data:~$ sudo aptitude install build-essential libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  libatk1.0-dev libcairo2-dev libexpat1-dev libfontconfig1-dev 
  libfreetype6-dev libglib2.0-dev libice-dev libpango1.0-dev libpng12-dev 
  libsm-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev 
  libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxrandr-dev 
  libxrender-dev x11proto-core-dev x11proto-fixes-dev x11proto-input-dev 
  x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev 
  x11proto-xinerama-dev xtrans-dev zlib1g-dev 
The following NEW packages will be installed:
  libatk1.0-dev libcairo2-dev libexpat1-dev libfontconfig1-dev 
  libfreetype6-dev libglib2.0-dev libgtk2.0-dev libice-dev libpango1.0-dev 
  libpng12-dev libsm-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev 
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev 
  libxrandr-dev libxrender-dev x11proto-core-dev x11proto-fixes-dev 
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev 
  x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev 
0 packages upgraded, 32 newly installed, 0 to remove and 0 not upgraded.
Need to get 7434kB of archives. After unpacking 28.3MB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libpng12-dev 1.2.8rel-5.1ubuntu0.1 [243kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main x11proto-core-dev 7.0.7-1 [78.3kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libice-dev 2:1.0.1-1ubuntu1 [49.9kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libsm-dev 2:1.0.1-1ubuntu1 [20.0kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libxau-dev 1:1.0.1-1 [10.3kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libxdmcp-dev 1:1.0.1-1 [13.6kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main x11proto-input-dev 1.3.2-3ubuntu1 [13.4kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main x11proto-xext-dev 7.0.2-4ubuntu1 [41.7kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libxext-dev 2:1.0.1-1ubuntu1 [73.7kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main x11proto-kb-dev 1.0.3-0ubuntu1 [26.5kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main xtrans-dev 1.0.1-1 [58.8kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libx11-dev 2:1.0.3-0ubuntu4 [1181kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main x11proto-render-dev 2:0.9.2-3ubuntu1 [6556B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libxrender-dev 1:0.9.1-0ubuntu1 [23.3kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main x11proto-fixes-dev 1:4.0-0.1ubuntu1 [5500B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libxfixes-dev 1:4.0.1-0ubuntu1 [11.0kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libxcursor-dev 1.1.7-0ubuntu1 [29.7kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libexpat1-dev 1.95.8-3.2 [126kB]     
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main zlib1g-dev 1:1.2.3-13ubuntu2 [407kB] 
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libfreetype6-dev 2.2.1-5 [640kB]     
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libfontconfig1-dev 2.3.2-7ubuntu2 [248kB]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libxft-dev 2.1.10-1ubuntu1 [55.5kB]  
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libxi-dev 2:1.0.1-0ubuntu1 [62.4kB]  
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main x11proto-xinerama-dev 1.1.2-3ubuntu1 [4956B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libxinerama-dev 2:1.0.1-4build1 [4196B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main x11proto-randr-dev 1.1.2-3ubuntu1 [4664B]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libxrandr-dev 2:1.1.1-0ubuntu1 [14.5kB]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libglib2.0-dev 2.12.4-0ubuntu1 [533kB]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libatk1.0-dev 1.12.3-0ubuntu1 [109kB]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libcairo2-dev 1.2.4-1ubuntu2 [445kB] 
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libpango1.0-dev 1.14.5-0ubuntu1 [321kB]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libgtk2.0-dev 2.10.6-0ubuntu1 [2572kB]
Fetched 7434kB in 40s (183kB/s)                                                 
Extracting templates from packages: 100%
Selecting previously deselected package x11proto-core-dev.
(Reading database ... 114178 files and directories currently installed.)
Unpacking x11proto-core-dev (from .../x11proto-core-dev_7.0.7-1_all.deb) ...
Selecting previously deselected package libice-dev.
Unpacking libice-dev (from .../libice-dev_2%3a1.0.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libsm-dev.
Unpacking libsm-dev (from .../libsm-dev_2%3a1.0.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libxau-dev.
Unpacking libxau-dev (from .../libxau-dev_1%3a1.0.1-1_i386.deb) ...
Selecting previously deselected package libxdmcp-dev.
Unpacking libxdmcp-dev (from .../libxdmcp-dev_1%3a1.0.1-1_i386.deb) ...
Selecting previously deselected package x11proto-input-dev.
Unpacking x11proto-input-dev (from .../x11proto-input-dev_1.3.2-3ubuntu1_all.deb) ...
Selecting previously deselected package x11proto-xext-dev.
Unpacking x11proto-xext-dev (from .../x11proto-xext-dev_7.0.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxext-dev.
Unpacking libxext-dev (from .../libxext-dev_2%3a1.0.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package x11proto-kb-dev.
Unpacking x11proto-kb-dev (from .../x11proto-kb-dev_1.0.3-0ubuntu1_all.deb) ...
Selecting previously deselected package xtrans-dev.
Unpacking xtrans-dev (from .../xtrans-dev_1.0.1-1_all.deb) ...
Selecting previously deselected package libx11-dev.
Unpacking libx11-dev (from .../libx11-dev_2%3a1.0.3-0ubuntu4_i386.deb) ...
Selecting previously deselected package x11proto-render-dev.
Unpacking x11proto-render-dev (from .../x11proto-render-dev_2%3a0.9.2-3ubuntu1_all.deb) ...
Selecting previously deselected package libxrender-dev.
Unpacking libxrender-dev (from .../libxrender-dev_1%3a0.9.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package x11proto-fixes-dev.
Unpacking x11proto-fixes-dev (from .../x11proto-fixes-dev_1%3a4.0-0.1ubuntu1_all.deb) ...
Selecting previously deselected package libxfixes-dev.
Unpacking libxfixes-dev (from .../libxfixes-dev_1%3a4.0.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package libxcursor-dev.
Unpacking libxcursor-dev (from .../libxcursor-dev_1.1.7-0ubuntu1_i386.deb) ...
Selecting previously deselected package libexpat1-dev.
Unpacking libexpat1-dev (from .../libexpat1-dev_1.95.8-3.2_i386.deb) ...
Selecting previously deselected package zlib1g-dev.
Unpacking zlib1g-dev (from .../zlib1g-dev_1%3a1.2.3-13ubuntu2_i386.deb) ...
Selecting previously deselected package libfreetype6-dev.
Unpacking libfreetype6-dev (from .../libfreetype6-dev_2.2.1-5_i386.deb) ...
Selecting previously deselected package libfontconfig1-dev.
Unpacking libfontconfig1-dev (from .../libfontconfig1-dev_2.3.2-7ubuntu2_i386.deb) ...
Selecting previously deselected package libxft-dev.
Unpacking libxft-dev (from .../libxft-dev_2.1.10-1ubuntu1_i386.deb) ...
Selecting previously deselected package libxi-dev.
Unpacking libxi-dev (from .../libxi-dev_2%3a1.0.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package x11proto-xinerama-dev.
Unpacking x11proto-xinerama-dev (from .../x11proto-xinerama-dev_1.1.2-3ubuntu1_all.deb) ...
Selecting previously deselected package libxinerama-dev.
Unpacking libxinerama-dev (from .../libxinerama-dev_2%3a1.0.1-4build1_i386.deb) ...
Selecting previously deselected package x11proto-randr-dev.
Unpacking x11proto-randr-dev (from .../x11proto-randr-dev_1.1.2-3ubuntu1_all.deb) ...
Selecting previously deselected package libxrandr-dev.
Unpacking libxrandr-dev (from .../libxrandr-dev_2%3a1.1.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package libglib2.0-dev.
Unpacking libglib2.0-dev (from .../libglib2.0-dev_2.12.4-0ubuntu1_i386.deb) ...
Selecting previously deselected package libatk1.0-dev.
Unpacking libatk1.0-dev (from .../libatk1.0-dev_1.12.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package libpng12-dev.
Unpacking libpng12-dev (from .../libpng12-dev_1.2.8rel-5.1ubuntu0.1_i386.deb) ...
Selecting previously deselected package libcairo2-dev.
Unpacking libcairo2-dev (from .../libcairo2-dev_1.2.4-1ubuntu2_i386.deb) ...
Selecting previously deselected package libpango1.0-dev.
Unpacking libpango1.0-dev (from .../libpango1.0-dev_1.14.5-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgtk2.0-dev.
Unpacking libgtk2.0-dev (from .../libgtk2.0-dev_2.10.6-0ubuntu1_i386.deb) ...
Setting up x11proto-core-dev (7.0.7-1) ...
Setting up libice-dev (1.0.1-1ubuntu1) ...
Setting up libsm-dev (1.0.1-1ubuntu1) ...
Setting up libxau-dev (1.0.1-1) ...
Setting up libxdmcp-dev (1.0.1-1) ...
Setting up x11proto-input-dev (1.3.2-3ubuntu1) ...
Setting up x11proto-xext-dev (7.0.2-4ubuntu1) ...
Setting up x11proto-kb-dev (1.0.3-0ubuntu1) ...
Setting up xtrans-dev (1.0.1-1) ...
Setting up x11proto-render-dev (0.9.2-3ubuntu1) ...
Setting up x11proto-fixes-dev (4.0-0.1ubuntu1) ...
Setting up libexpat1-dev (1.95.8-3.2) ...

Setting up zlib1g-dev (1.2.3-13ubuntu2) ...
Setting up libfreetype6-dev (2.2.1-5) ...

Setting up libfontconfig1-dev (2.3.2-7ubuntu2) ...
Setting up x11proto-xinerama-dev (1.1.2-3ubuntu1) ...
Setting up x11proto-randr-dev (1.1.2-3ubuntu1) ...
Setting up libglib2.0-dev (2.12.4-0ubuntu1) ...
Setting up libatk1.0-dev (1.12.3-0ubuntu1) ...
Setting up libpng12-dev (1.2.8rel-5.1ubuntu0.1) ...

Setting up libxext-dev (1.0.1-1ubuntu1) ...
Setting up libx11-dev (1.0.3-0ubuntu4) ...
Setting up libxrender-dev (0.9.1-0ubuntu1) ...
Setting up libxfixes-dev (4.0.1-0ubuntu1) ...
Setting up libxcursor-dev (1.1.7-0ubuntu1) ...
Setting up libxft-dev (2.1.10-1ubuntu1) ...
Setting up libxi-dev (1.0.1-0ubuntu1) ...
Setting up libxinerama-dev (1.0.1-4build1) ...
Setting up libxrandr-dev (1.1.1-0ubuntu1) ...
Setting up libcairo2-dev (1.2.4-1ubuntu2) ...
Setting up libpango1.0-dev (1.14.5-0ubuntu1) ...
Setting up libgtk2.0-dev (2.10.6-0ubuntu1) ...
petey@Data:~$ cd ~/xe-bin
petey@Data:~/xe-bin$ sudo make
/usr/bin/ld: cannot find -lasound
collect2: ld returned 1 exit status
make: *** [xe] Error 1
petey@Data:~/xe-bin$ sudo make install
[: 37: ==: unexpected operator
Must be logged on as root.
petey@Data:~/xe-bin$ 



ok now what happened?

---

### Post by grte on 2006-11-21
> **TheRingmaster said:**
> ok now what happened?

Hmm...For some reason, sudo doesn't seem to be enough, and I think  you might need the alsa dev package too.  Try this:

```
sudo -i
cd /to/the/directory
apt-get install libasound2-dev
make
make install
logout
```

---

### Post by TheRingmaster on 2006-11-22
> **grte said:**
> Hmm...For some reason, sudo doesn't seem to be enough, and I think  you might need the alsa dev package too.  Try this:

```
sudo -i
cd /to/the/directory
apt-get install libasound2-dev
make
make install
logout
```

> petey@Data:~$ sudo -i
root@Data:~# cd ~/desktop/xe-bin
-bash: cd: /root/desktop/xe-bin: No such file or directory
root@Data:~# cd ~/xe-bin
root@Data:~/xe-bin# aptitude install libasound2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  libasound2-dev 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 467kB of archives. After unpacking 1819kB will be used.
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libasound2-dev 1.0.11-7ubuntu3 [467kB]
Fetched 467kB in 3s (138kB/s)          
Selecting previously deselected package libasound2-dev.
(Reading database ... 116780 files and directories currently installed.)
Unpacking libasound2-dev (from .../libasound2-dev_1.0.11-7ubuntu3_i386.deb) ...
Setting up libasound2-dev (1.0.11-7ubuntu3) ...

root@Data:~/xe-bin# make
/usr/bin/ld: cannot find -lXv
collect2: ld returned 1 exit status
make: *** [xe] Error 1
root@Data:~/xe-bin# make install
[: 37: ==: unexpected operator
Must be logged on as root.
root@Data:~/xe-bin# logout
petey@Data:~$ 



ok now what again

---

### Post by grte on 2006-11-22
Okay, looked around a bit, and it seems you'll need libxv-dev, well well, so ```
sudo apt-get install libxv-dev
``` and try again.

---

### Post by TheRingmaster on 2006-11-23
> **grte said:**
> Okay, looked around a bit, and it seems you'll need libxv-dev, well well, so ```
sudo apt-get install libxv-dev
``` and try again.
> petey@Data:~$ sudo aptitude install libxv-dev
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  x11proto-video-dev 
The following NEW packages will be installed:
  libxv-dev x11proto-video-dev 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 40.3kB of archives. After unpacking 270kB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main x11proto-video-dev 2.2.2-3ubuntu1 [9400B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libxv-dev 2:1.0.1-3ubuntu1 [30.9kB]
Fetched 40.3kB in 0s (45.6kB/s)         
Selecting previously deselected package x11proto-video-dev.
(Reading database ... 117186 files and directories currently installed.)
Unpacking x11proto-video-dev (from .../x11proto-video-dev_2.2.2-3ubuntu1_all.deb) ...
Selecting previously deselected package libxv-dev.
Unpacking libxv-dev (from .../libxv-dev_2%3a1.0.1-3ubuntu1_i386.deb) ...
Setting up x11proto-video-dev (2.2.2-3ubuntu1) ...
Setting up libxv-dev (1.0.1-3ubuntu1) ...
petey@Data:~$ sudo -i
root@Data:~# cd ~/xe-bin
root@Data:~/xe-bin# make
/usr/bin/ld: cannot find -lXxf86vm
collect2: ld returned 1 exit status
make: *** [xe] Error 1
root@Data:~/xe-bin# make install
[: 37: ==: unexpected operator
Must be logged on as root.
root@Data:~/xe-bin# logout
petey@Data:~$ 

still no luck

---

### Post by grte on 2006-11-23
> **TheRingmaster said:**
> still no luck

Okay, just working through the deps, looks like.

Try apt-getting libxxf86vm1 and libxxf86vm-dev as well.

---

### Post by TheRingmaster on 2006-11-23
> **grte said:**
> Okay, just working through the deps, looks like.

Try apt-getting libxxf86vm1 and libxxf86vm-dev as well.

couldn't find the first one, but the second one I installed. looks like we are gaining ground. > petey@Data:~$ sudo -i
root@Data:~# cd ~/xe-bin
root@Data:~/xe-bin# make
root@Data:~/xe-bin# make install
[: 37: ==: unexpected operator
Must be logged on as root.
root@Data:~/xe-bin# 



---

### Post by grte on 2006-11-23
> **TheRingmaster said:**
> couldn't find the first one, but the second one I installed. looks like we are gaining ground.

That error I'm not sure about, seeing as you are logged in as root.  Does xe have a forum?  I'd try asking there.

---

### Post by TheRingmaster on 2006-11-23
I have contacted the maintainer of the xe-emulator. hopefully he can help more.

---

### Post by TheRingmaster on 2006-11-23
I could do the installation the hard way: 
 
Install to system directory: 
[LIST=1]
[*]login as root
[*]'make' to link the software
[*]'mkdir /usr/local/lib/xe' to create system directory
[*]'mv xe rc modules manual /usr/local/lib/xe' to move files to system directory
[*]'ln -sf /usr/local/lib/xe/xe /usr/local/bin/xe' to link binary into system path[/LIST]Install to user directory: 
[LIST=1]
[*]'make' to link the software
[*]'mkdir ~/.xe' to create local directory
[*]'mv xe rc modules manual ~/.xe' to move files to local directory
[*]link or move ~/.xe/xe' to your local bin directory[/LIST]

---

### Post by TheRingmaster on 2006-11-23
I got it finally.

just had to manually drag and drop files. what a pain.

---

