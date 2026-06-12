---
title: "Building a Distro with Citrix Receiver"
date: 2015-10-07
forum: General Help
---

### Post by Ian_Selby on 2015-10-07
Hi All,

I have a couple of issues I am hoping to get some assistance with but to put it into context I will start with some background. A couple of years back I put together an installation of ubuntu 12.04.1 LTS, with little to no customisation other than installing citrix receiver ( version 12.1 ). Due to a need to upgrade the receiver to version 13.2 I want to effectively put together another Ubuntu usb installer like I did first time round. 

The way in which I did it the first time round was simply to install Ubuntu, install the receiver and test and then I used RemasterSys to build an ISO of the running system. I then used Universal USB Installer to turn put this ISO onto a bootable USB stick. Everything worked perfectly. Doing this a second time round not so much.

There are effectively two issues I am running into

[LIST=1]
[*]If I upgrade the receiver on one of our machines, it tests and works ok. However if I use remastersys and then use the ISO / bootable USB to install this onto a machine the installer gets so far (beyond copying files, and asking for user/admin details, language etc) and then crashes, throwing up an error 'The installer has crashed'
[*]If I simply use remastersys on an existing build without upgrading the receiver (just to see if this was the problem) the ISO build does not give the option to install, or rather it is listed in the boot menu, but when selected it just loads Ubuntu off the disk as per a live CD without trying to install it.
[/LIST]

I don't know if Remastersys is still being maintained, I am seeing some conflicting information on that, but I need a simple way to effectively build a machine with Ubuntu and citrix receiver on it and put this onto a usb drive so I can run around a bunch of machines and install it onto.

Very new to Linux and Ubuntu the initial procedure was done following a guide, so ideally need something simple like remastersys if possible.

Thanks for taking the time to read this.

Ian

---

### Post by tea for one on 2015-10-07
Remastersys is no longer being maintained.

Have a look at this alternative:- [https://launchpad.net/systemback](https://launchpad.net/systemback)

---

