---
title: "Not possible to install/run Google Earth on 14.04?"
date: 2014-11-15
forum: General Help
---

### Post by WB0HYQ on 2014-11-15
Using Ubuntu/Xubuntu 14.04 (with XFCE4.1 overlay) 64-bit.  I have been researching everywhere to find out how to install and run Google Earth on Ubuntu/Xubuntu 14.04.  There are quite a few "ways" to install and get it running and I've tried each and every one.  NONE of them work.  It appears I can install 'goodle-earth-stable' (according to dpkg), but it will NOT run.  I can use dpkg -r and uninstall google-earth-stable and the command will run correctly, but there just doesn'ty seem to be any way to get the package to run at all.  Ubuntu Tweak's version of Google Earth will hang Ubuntu Tweak until I kill it OR it will tell me there is a "stable version available" and then mess up installing it by telling me that it will not download and install a 32-bit package, so I am stuck there also.

Is there no way to get it running on this version of Ubuntu?

Bill

---

### Post by Toz on 2014-11-15
[This link]("http://www.webupd8.org/2014/04/install-google-earth-in-ubuntu-1404.html") worked for me a while ago when I tried.

---

### Post by WB0HYQ on 2014-11-15
It looks terribly complicated for something that should be fairly simple.  Given the mess Google made of the Google maps "upgrade", I'm not surprised that they complete blew their GE upgrade also.  I'll give this a try and report back.

Thanks, Toz,

Bill

---

### Post by WB0HYQ on 2014-11-15
BOOM.  Install exploded messily:

```

bill@bill-UBU:~/Downloads/Software$ sudo dpkg -i google-earth-stable_current_i386.deb
Selecting previously unselected package google-earth-stable.
(Reading database ... 274071 files and directories currently installed.)
Preparing to unpack google-earth-stable_current_i386.deb ...
Unpacking google-earth-stable (7.1.2.2041-r0) ...
dpkg: dependency problems prevent configuration of google-earth-stable:
 google-earth-stable depends on lsb-core (>= 3.2).dpkg: error processing package google-earth-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for menu (2.1.46ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Errors were encountered while processing:
 google-earth-stable
bill@bill-UBU:~/Downloads/Software$ 

```

The above system response came AFTER the below system response (which installed properly):

```

bill@bill-UBU:~$ sudo apt-get install libfontconfig1:i386 libx11-6:i386 libxrender1:i386 libxext6:i386 libgl1-mesa-glx:i386 libglu1-mesa:i386 libglib2.0-0:i386 libsm6:i386
[sudo] password for bill: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsm6:i386 is already the newest version.
libsm6:i386 set to manually installed.
libx11-6:i386 is already the newest version.
libx11-6:i386 set to manually installed.
libxext6:i386 is already the newest version.
libxext6:i386 set to manually installed.
libxrender1:i386 is already the newest version.
libxrender1:i386 set to manually installed.
libfontconfig1:i386 is already the newest version.
libfontconfig1:i386 set to manually installed.
libglib2.0-0:i386 is already the newest version.
libglib2.0-0:i386 set to manually installed.
The following extra packages will be installed:
  libegl1-mesa libegl1-mesa-drivers libgl1-mesa-glx libglapi-mesa
  libglapi-mesa:i386 libgles2-mesa libwayland-egl1-mesa
The following NEW packages will be installed:
  libglu1-mesa:i386
The following packages will be upgraded:
  libegl1-mesa libegl1-mesa-drivers libgl1-mesa-glx libgl1-mesa-glx:i386
  libglapi-mesa libglapi-mesa:i386 libgles2-mesa libwayland-egl1-mesa
8 upgraded, 1 newly installed, 0 to remove and 15 not upgraded.
Need to get 2,537 kB of archives.
After this operation, 512 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libgl1-mesa-glx amd64 10.1.3-0ubuntu0.2 [114 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libgl1-mesa-glx i386 10.1.3-0ubuntu0.2 [112 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libwayland-egl1-mesa amd64 10.1.3-0ubuntu0.2 [6,470 B]
Get:4 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libegl1-mesa-drivers amd64 10.1.3-0ubuntu0.2 [1,995 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libgles2-mesa amd64 10.1.3-0ubuntu0.2 [12.5 kB]
Get:6 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libglapi-mesa i386 10.1.3-0ubuntu0.2 [21.3 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libglapi-mesa amd64 10.1.3-0ubuntu0.2 [21.4 kB]
Get:8 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libegl1-mesa amd64 10.1.3-0ubuntu0.2 [59.0 kB]
Get:9 http://archive.ubuntu.com/ubuntu/ trusty/main libglu1-mesa i386 9.0.0-2 [195 kB]
Fetched 2,537 kB in 13s (189 kB/s)                                             
(Reading database ... 274069 files and directories currently installed.)
Preparing to unpack .../libgl1-mesa-glx_10.1.3-0ubuntu0.2_i386.deb ...
De-configuring libgl1-mesa-glx:amd64 (10.1.3-0ubuntu0.1) ...
Unpacking libgl1-mesa-glx:i386 (10.1.3-0ubuntu0.2) over (10.1.3-0ubuntu0.1) ...
Preparing to unpack .../libgl1-mesa-glx_10.1.3-0ubuntu0.2_amd64.deb ...
Unpacking libgl1-mesa-glx:amd64 (10.1.3-0ubuntu0.2) over (10.1.3-0ubuntu0.1) ...
Preparing to unpack .../libwayland-egl1-mesa_10.1.3-0ubuntu0.2_amd64.deb ...
Unpacking libwayland-egl1-mesa:amd64 (10.1.3-0ubuntu0.2) over (10.1.3-0ubuntu0.1) ...
Preparing to unpack .../libegl1-mesa-drivers_10.1.3-0ubuntu0.2_amd64.deb ...
Unpacking libegl1-mesa-drivers:amd64 (10.1.3-0ubuntu0.2) over (10.1.3-0ubuntu0.1) ...
Preparing to unpack .../libgles2-mesa_10.1.3-0ubuntu0.2_amd64.deb ...
Unpacking libgles2-mesa:amd64 (10.1.3-0ubuntu0.2) over (10.1.3-0ubuntu0.1) ...
Preparing to unpack .../libglapi-mesa_10.1.3-0ubuntu0.2_amd64.deb ...
De-configuring libglapi-mesa:i386 (10.1.3-0ubuntu0.1) ...
Unpacking libglapi-mesa:amd64 (10.1.3-0ubuntu0.2) over (10.1.3-0ubuntu0.1) ...
Preparing to unpack .../libglapi-mesa_10.1.3-0ubuntu0.2_i386.deb ...
Unpacking libglapi-mesa:i386 (10.1.3-0ubuntu0.2) over (10.1.3-0ubuntu0.1) ...
Preparing to unpack .../libegl1-mesa_10.1.3-0ubuntu0.2_amd64.deb ...
Unpacking libegl1-mesa:amd64 (10.1.3-0ubuntu0.2) over (10.1.3-0ubuntu0.1) ...
Selecting previously unselected package libglu1-mesa:i386.
Preparing to unpack .../libglu1-mesa_9.0.0-2_i386.deb ...
Unpacking libglu1-mesa:i386 (9.0.0-2) ...
Setting up libglapi-mesa:amd64 (10.1.3-0ubuntu0.2) ...
Setting up libglapi-mesa:i386 (10.1.3-0ubuntu0.2) ...
Setting up libgl1-mesa-glx:amd64 (10.1.3-0ubuntu0.2) ...
Setting up libgl1-mesa-glx:i386 (10.1.3-0ubuntu0.2) ...
Setting up libegl1-mesa:amd64 (10.1.3-0ubuntu0.2) ...
Setting up libwayland-egl1-mesa:amd64 (10.1.3-0ubuntu0.2) ...
Setting up libegl1-mesa-drivers:amd64 (10.1.3-0ubuntu0.2) ...
Setting up libgles2-mesa:amd64 (10.1.3-0ubuntu0.2) ...
Setting up libglu1-mesa:i386 (9.0.0-2) ...
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
bill@bill-UBU:~$ cd Downloads/Software

```

I've been getting this, or other forms of it, every attempt I make to get this installed.  Apparently, it can be done, but I cannot find out HOW to do it.

Bill

---

### Post by WB0HYQ on 2014-11-15
I have absolutely NO idea how it happened, but after the Software Installer crashed four times, and I ran apt-get install -f twice, I could start Google Eartch from the command line as "google-earth" on my 64-bit system.

Since I use Cairo Dock, I had it "make it a launcher" (but that failed) so I dragged and dropped the Google Earth entry in the Applications Menu to the dock.  Now, when I click it, Googe Earth starts up.

Go figure.

I wonder what will break it once any new updates are installed, or some package remover decides that a package required for Google Earth "Isn't needed" and removes it - thus breaking GE again.

Bill

---

### Post by mc4man on 2014-11-15
Your orig issue was this - 
"google-earth-stable depends on lsb-core  (>= 3.2).dpkg: error processing package google-earth-stable"
(- dpkg does not resolve dependencies so lsb-core should have been installed   before trying to install GE, something webupd8 fails to note...

---

### Post by WB0HYQ on 2014-11-15
Well, that's the strange part, then.  I don't know how it got installed, but according to dpkg -L, lsb-core is installed now.

What's important is that GE runs now.  I am hoping it isn't too fragile an environment so that the next update will wipe out its functionality once again (it used to run under 12.04 but got broken when 14.04 came along).

Thanks for everyone's help.

Bill

---

