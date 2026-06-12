---
title: "New Programs"
date: 2007-10-21
forum: General Help
---

### Post by PAULLYN on 2007-10-21
I've just installed Ubuntu as a dual boot system a coupla days ago with my XP Pro and as all my computing up till now has been with Windows There's a few small hiccups. Can anybody help with installing new programs. I've used the Add/Remove Programs Application a few times and think it's great, very easy. But. I have a problem installing programs that aren't on the Add/Remove Programs list. Specifically I use the Unwired network and want to run the program to fine tune the position of my wireless modem. Program called Navini Diagnostics. I have downloaded the .bin file from the Navini website which says its for Linux. Have the .bin file stored on my hard drive but can't figure out how to install. Have tried Synaptic Packet Manager with no success and am a bit out of my depth with the Terminal Commands. I love Ubuntu but need to fine tune my modem for the best signal and at the moment I have to boot to Windows to fine tune the modem then reboot to Ubuntu. Much hassle. Any help would be appreciated. Thanks.

---

### Post by PAULLYN on 2007-10-22
Well I sorted out the command line and ran the install but got an error message, some files could not be found. Here is a copy. I have left the command line out cause I figure if I got it to do this I must be doing something right, I used sudo and got a password prompt which all went well. Then....

Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.11371/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory. 

Any ideas. Is the linux .bin file different in some way to what I need for Ubuntu. I trudt the file I downloaded it came from the company's website and I have downloaded and used the Windows files for the same program with no problems on previous occasions.

---

### Post by larryfroot on 2007-10-22
I think that the installer has been set up to look for the libraries in locations where they are not stored by default in ubuntu. To find out where the installer is looking for the libraries ( which needed to be installed by synaptic on my setup for a start. Just run a search to find them in synaptic) you are going to have to contact the company concerned. Then - and I would think - only think, mind you - that it would be safe to copy (for gods sake, **don't move** them!) the libraries to the folders where the installer is looking for them. 

Thats my own personal take..that the installer has been built to run with a single distro in mind and left at that, and as different distro's often have different default locations for libraries etc...I moved the .bin file to /opt and tried from there as well...but same result. 

So perhaps you are going to have to be outraged of tunbridge wells when contacting navini.

---

### Post by PAULLYN on 2007-10-23
Thank You larryfroot, that pretty much clarifies it in my mind. Sort of. I can understand what you say about libraries not being where Ubuntu looks for them as this may be different from where say Red Hat would store the same sort of info. I am still trying to register with the Navini website to post a few questions on their forum pages. I have sent an email to the Tech man listed on their website asking how to register. Thanks for the help mate. Paul.

---

### Post by larryfroot on 2007-10-24
There is usually a script containing the paths that the installer will go along to get to the libraries or anything else required. Believe me I am no expert, so don't be too surprised if the truth is different, but I remember hacking a couple of scripts so an installer knew where to look a few years ago. It is frustrating at times, but I think Linux puts the user back into power - and that requires learning. For us all, no matter how many times one has recompiled the kernel! 

I hope you get it sorted. Just thought this...is it worth going into synaptic to search for a specific prog that will do the job of the software you are looking for? There are a host of specialist dedicated applications out there, a lot of them are only designed to do one job, but to that job well. 

All the best and if you like, tell me how it all went. Good luck, LF

---

### Post by jemtallon on 2008-02-05
I'm having the same issue with the Navini Diagnostics program in Ubuntu. I have found if you set the LAX_DEBUG variable to 0 the installer will give you much more info on the problem. To do that, open up a command line window and enter:

export LAX_DEBUG=0
./NavDiag_linux.bin

I'll try digging a little deeper into it and post a solution if I find one.

---

