---
title: "Java fails to install on newly-created USB Flash-Drive-Bootable Gutsy 7.10"
date: 2008-01-29
forum: General Help
---

### Post by ACLBandit on 2008-01-29
Okay, so I finally got tired of using the crappy Windows Vista computers on campus with their 5 minute login times and all of the silliness that still comes with Vista. I decided that I would make a nifty little flash-bootable version of Ubuntu Gutsy that somewhat mirrors the functionality of my own personal desktop computer to use there; I can install the linux vpn client to connnect to their network, so I shouldn't have any problems at all.

I used a hybrid of the following two tutorials (mainly because the file at the end of the first install made me a bit nervous.):
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/")
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")

However, though I am close to being ready, I still lack the only thing that I honestly *need* to convert one of those monster PCs on campus into a temporary linux box of doom: JDK and java development tools.

I would like to have installed three things: The JDK, obviously, and Netbeans 6.0 and Eclipse. However, neither of the last two of the three items will work without the first. 

I need JDK.

However, if I use synaptic OR apt-get to install, I get the following output:
```
sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  sun-java6-bin sun-java6-jre
Suggested packages:
  binfmt-support sun-java6-demo sun-java6-doc sun-java6-source
  sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  sun-java6-bin sun-java6-jdk sun-java6-jre
0 upgraded, 3 newly installed, 0 to remove and 78 not upgraded.
Need to get 0B/42.3MB of archives.
After unpacking 126MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package sun-java6-bin.
(Reading database ... 92898 files and directories currently installed.)
Unpacking sun-java6-bin (from .../sun-java6-bin_6-03-0ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-jre.
Unpacking sun-java6-jre (from .../sun-java6-jre_6-03-0ubuntu2_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-jdk.
Unpacking sun-java6-jdk (from .../sun-java6-jdk_6-03-0ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Setting up sun-java6-jre (6-03-0ubuntu2) ...

Setting up sun-java6-bin (6-03-0ubuntu2) ...
/usr/lib/jvm/java-6-sun-1.6.0.03/bin/java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 127
Setting up sun-java6-jdk (6-03-0ubuntu2) ...

Errors were encountered while processing:
 sun-java6-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

However, I did not yet despair: I apt-get removed to make all the java funk get off my pathetic 2gig flash drive, and then proceeded with an attempt to install manually.

...

Okay, so now I have a nifty little .sh file. Chmod +x jdk-6u4-nb-6_0-linux.sh... okay, great.

./*.sh.

Oh, nifty, a GUI installer... I tried installing it default as both regular user and as root in multiple locations on the filesystem, including my own home drive; however, no m
atter what, with this I get the following useless message that doesn't help me in the GUI installer:

:!:JDK Update 4 is set up to be installed to /xxx/xxx/jdk1.6.0_04 which does not belong to any of the filesystem roots. 

Great. I need to make it install to the filesystem roots... I would think the / directory, or the "filesystem" icon under computer, but... apparently not.

Assistance would be appreciated ^_^

---

### Post by dcstar on 2008-01-30
> **ACLBandit said:**
> 
...........
Assistance would be appreciated ^_^

All Java installs have a section where you are initially prompted to accept their licence terms, if this does not happen then the install fails.

Do this in a terminal and then try the Java install again (I use the Gnome option myself):

```
sudo dpkg-reconfigure debconf
```

---

### Post by ACLBandit on 2008-01-30
Okay, tried that and the command line output is identical. I tried changing the "ignore messages below" setting to low, but to no avail. I already accepted the license agreement, though, at least two other times when trying to install.

---

### Post by p3t3y on 2008-03-30
im having the EXACT same problem and wondered if someone figured this one out....i have no hard drive and probably for a few months all i have is a 2 gig pen drive and my copy of 7.10 gutsy (wich i cant get java running on either cause i get the same exact erorrs)....i have read every tutorial on java on ubuntu and every problem post thats on here to do with java....i didnt wanna create a new thread so i figured i would bump this one..

---

### Post by cfriedt on 2008-04-01
I'm having the exact same problem. I've set up my persistent usb key based on Gutsy. 
Error is below.

Setting up sun-java6-bin (6-03-0ubuntu2) ...
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 2

The strange part is that the jdk installs correctly, but it keeps complaining about not being able to locate libjava.so, even though LD_LIBRARY_PATH is set, all of the update-alternatives have been properly set, etc.

I'm normally a gentoo person but thought that I would try out Ubuntu on a live usb while my laptop was in for repairs -- it's a total pain in the ***. I thought that because Ubuntu uses binary packages that it would be a faster install, but that's completely not the case.

Gentoo is much more stable and also easier to work with. 

Or maybe it's just java support that really blows with Ubuntu.

who knows :P

---

