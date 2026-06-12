---
title: "Video file on command line install on Dectop"
date: 2008-02-13
forum: General Help
---

### Post by nutts4life on 2008-02-13
Hi there,

I having a problem with instalingl the command line xubuntu so i can build a wm on top.

The full xubuntu package runs too slow on my AMD Dectop PIC, so i want to install it this way.

Here's the problem:

This wiki outlines the installation process and the problem: [http://dectop.nfshost.com/wiki/index...untu_on_decTOP](http://dectop.nfshost.com/wiki/index...untu_on_decTOP)

The page describes what do to if you can't get into the full xubuntu install, by: booting back into dectop using the install usb stick and modifying the xorg.conf with the driver = "amd".
When i tried to run the recovery mode with the xubuntu full install it failed.

This problem occurs when i can't boot up into my newly installed command line. It fails when it tries to load the hardware drivers (the screen goes a funny colour).

With the command line install there is no xorg. so i can't use the fix in the wiki.

I'm not sure how all this works, but does the command line have some kind of video configuration?

Would be great if anybody could help!

nutts4life

---

### Post by nutts4life on 2008-02-13
bumpity bumpity

---

### Post by pointone on 2008-02-13
Link is broken...

```
apt-get install xserver-xorg
```

... to install X.Org, and:

```
Xorg -configure
```

... or:

```
dpkg-reconfigure xserver-xorg -phigh
```

... to (re)configure and create an xorg.conf file.

---

### Post by nutts4life on 2008-02-13
Hi there,

Thanks for your swift reply.

Unfortuately i can't run any apt-get as i cannot get into the system, the only thing i can do is use the shell provided by the install USB stick. This has no environment set nor network connections.

In fact, in order to access the drive on which xubuntu is mounted i have to mount the disk myself.

Unless there is a good moment during the install process where the environment is set up and the network connection is acheived then i can't do this.

Any ideas?

nutts4life

---

### Post by nutts4life on 2008-02-18
Just bumping this again. as i can't beleive this isn't easy to fix.

Just to remind you:
I've done a USB install of xubuntu command line on a AMD Geode board and HDD.

The install was successful, but when i try and boot the boot fails at detecting hardware stage.

This is a known problem during a full xubuntu install on this machine and the fix is to reboot using the usb installer and quite to command line.

Once you are at command line you can modify the xorg to read device = "amd".

But for some reason this also affects the command line install for some reason. Even though this does NOT have xorg installed.

So what do i do?

I can't install xorg as i can't get to the command line (nor recovery), i can only edit files.
I've tried running the usb install again and detecting the network, then setting up my environment to run apt-get by hand. But that failed becuase i had to mount my hdd for installation. This meant sources.list wasn't at /etc/apt/s....

Any ideas, would be great.

Thanks,

n4l

---

### Post by caeserjk02 on 2008-02-19
Boot the dectop with your USB disk and choose to recover your system. You will go through a short setup phase which includes networking config. You will be prompted as to which filesystem you would like to chroot to. Select the hard disk that you have installed your system to. Once you have a CLI on your target drive, then proceed to install xorg using apt. 

Be sure to toss the network card that comes with these devices. They are crap. They overheat and tend to short out. 

We are currently running about 30 of these machines in a manufacturing/warehouse environment and have chosen to use [COLOR="Blue"]_[ASUS WL-167g]("http://www.newegg.com/Product/Product.aspx?Item=N82E1683332010")_[/COLOR] wifi adapters. These have proven to be very reliable and work great on these machines. Plus the drivers are in the latest Xubuntu release.

---

