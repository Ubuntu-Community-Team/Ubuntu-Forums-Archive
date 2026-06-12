---
title: "Qs: KDE volume, versions, finding apps"
date: 2006-12-10
forum: General Help
---

### Post by sunspots on 2006-12-10
Hi,
I thought it is easier to one message with these short questions.

1) I have installed KDE desktop, but can't find how to adjust the speaker volume. Is there a special app that needs to be installed?

2) in the CLI / server environment I want to check what versions of  software I have installed,EG, PHP, Apache, mySQL, etc. Is there an application that you can run with an argument of the application to give you the version? The ones I listed above are my specific requirements, but do want to know if there is a generic way.

3) How do I find in a CLI (command line interface) environment what applications are available to install? For example, I want to find and install software for Palm TREO.

Thanks for taking the time to read and reply.

---

### Post by bettlebrox on 2006-12-10
1) kmix controls the volume. I haven't used KDE in a while, but I think you need to right-click on the task bar to start it. Or just try starting it from the command-line.

For questions 2 & 3, look at the man page for apt-cache & apt-get. You can do "apt-cache search somethin" to search for packages, and then "apt-cache show packagename" to show details, including version numbers, of an installed package.

For example, I what to search for apache (returns a tonnes of stuff):
$ apt-cache search apache|more
ant - Java based build tool like make
apache2 - next generation, scalable, extendable web server
apache2-common - next generation, scalable, extendable web server
...

Then:
$ apt-cache show apache2
Package: apache2
Priority: optional
Section: web
Installed-Size: 80
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Original-Maintainer: Debian Apache Maintainers <debian-apache@lists.debian.org>
Architecture: i386
Version: 2.0.55-4ubuntu4
...

See here for more docs on apt:
[http://www.us.debian.org/doc/manuals/apt-howto/ch-search.en.html#s-cache](http://www.us.debian.org/doc/manuals/apt-howto/ch-search.en.html#s-cache)

Also, aptitude is useful text-based tools for installing & searching packages.

---

### Post by sunspots on 2006-12-11
Hi Bettlebrox
That was a big help. kmix wasn't available when I did a right click. But got it started from the command line.

Funny though, as I started from the command line I got the following but the application still started. Any clues?

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


I'll have a look at the command apt-cache.

---

### Post by Lord Illidan on 2006-12-11
> **sunspots said:**
> 

Funny though, as I started from the command line I got the following but the application still started. Any clues?

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


Have a look at your /etc/X11/xorg.conf . There are a few lines you might want to delete as they refer to Wacom tablets, added by default in the installer. If you want, post your xorg.conf here, and I'll tell you what to comment out.

---

### Post by sunspots on 2006-12-11
Hi Lord Illiad
Thanks for the tip and the offer.

I have looked in the file and commented the following.

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

These were the only lines in the file with Wacom.

Thanks

---

### Post by sunspots on 2006-12-11
I rebooted the PC and got a message that it couldn't start the X-Server. I logged in via the terminal and removed the comments I added and rebooted. I got the login GUI again. Back to normal.

Did mis-comment something in the list I gave above?
Thanks

---

### Post by bettlebrox on 2006-12-11
I don't think having Wacom listed in you xorg.conf will affect you sound. Kmix is complaining about the sound device. 

Does sound work?

---

### Post by sunspots on 2006-12-11
Sound is working. 

I am getting the same error when I entered into KWrite from the command line.

---

