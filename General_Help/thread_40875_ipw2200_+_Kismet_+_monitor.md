---
title: "ipw2200 + Kismet + monitor"
date: 2005-06-10
forum: General Help
---

### Post by MrSandman on 2005-06-10
i'm a noob here so go easy.
when configuring my gold card in ubuntu i noticed that i had monitor mode available on eth1. i had just upgraded to the latest firmware.

Intell have released new firmware (2.3) w/ rfmon.
> > so the rfmon (beta) support is now enabled
> > in the new 1.0.4 release of the ipw2200 drivers 

 [http://ipw2200.sourceforge.net/#news](http://ipw2200.sourceforge.net/#news)

 i wondered if kismet would work under the ipw2200 it wouldnt. 
so i went to the kismet site and discovered that support for ipw2200 monitor mode has been incorporated in the kismet_devl.
has anyone got this to work under umbuntu??
im gonna try.

Download the latest development code using Subversion with svn co [http://svn.kismetwireless.net/code/trunk](http://svn.kismetwireless.net/code/trunk) kismet-devel



May 17 2005  devel  Added ipw2200 support with temporary sw_reset support to try
                     to come out of monitor mode.  You'll need the 1.0.4 drivers
                     and new firmware, and you can force a reset of the card by
                     reloading the drivers
                    Added ipw2200 to fuzzy crypt list
                    Tweaked IP detection to not attempt to process IPs for any
                     packet associated with an encrypted network

May 18 2005  devel  Backed out my BROKEN ipw2200 sw_reset and followed James' 
                     advice to set the channel to 0 to restore scanning mode.
                     ipw2200 appears to come out of monitor mode cleanly now.
                    Fixed FloatChan2Int not handling absolute channels from the
                     driver layer.  I thought I'd merged a patch from someone to
                     do just this, but...
                    Dropped packet counter no longer includes phy frames

May 25 2005  devel  Configure changes for openbsd (pedro)
                    Tweaked cisci_wifix error message
                    Introduced a slight delay into the channel control process
                     for ipw2200 to prevent channel sets immediately on top of
                     one another causing the card to stop seeing packets.

May 27 2005  devel  Merged README updates and OpenBSD updates from Pedro
                    Merged OpenBSD channel display from pedro
                    Added ipw2915 packet source for centrinto a/g cards.
                     Same as the 2200, just has the default channels set to 
                     include 11a.
                    Fixed sigfpu failure if the default channel sets are
                     missing

---

### Post by MrSandman on 2005-06-12
In the latest official stable version of kismet was wrote that the modern driver of Intel PRO Wireless (ipw2200), very common in a lot of notebook with Intel Centrino, was not supported.
But there is a way to run kismet also with such driver...

Installing this program, for me, was not very "user friendly" ... it's a pain in the...so I wrote this little tutorial.
I use Ubuntu linux v. 5.0.4 and this guide is usefull expetially for my disto, but I think work also with others.

Last (warning) note: READ DOCUMENTS OF THE PROGRAMS LISTED ABOVE BEFORE MESS UP KERNEL AND DRIVERS. NO RESPONSABILITY FOR DAMAGES.

1) First step: check your driver.
You can do this making:

dmesg| grep ipw

and you must read something like
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver,0.19

The problem of this drivers with kismet is that you can't put your card in "monitor mode".
Try this:

iwconfig eth1 mode monitor

and you probably get an error.
Ok we need other drivers!


2)You must download the new driver (not the package! the tarball). You can download this here:
[http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.0.4.tgz](http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.0.4.tgz)

and untar it and go inside the new dir:
tar -xvfz ipw2200-1.0.4.tgz
cd ipw2200-1.0.4


3)Then you must remove old driver typing:
sh remove-old
See INSTALL file for more info


4)If you have ubuntu, you must edit the Makefile. Comment line like this:


# ifndef CONFIG_IPW2200 <---- Comment me
EXTERNAL_BUILD=y
CONFIG_IPW2200=m
CONFIG_IPW_DEBUG=y
CONFIG_IPW_MONITOR=y
# Experimental QoS support.
CONFIG_IPW_QOS=y
# endif  <---- Me also!

This is because there is a misunderstanding between the kernel of Ubuntu about this symbol and these definition.

5)If you have Ubuntu, install linux-headers.
You must have some files now in /lib/modules/version_of_kernel/build/

6) Download the new firmware 1.3 from this site


[http://ipw2200.sourceforge.net/firmware.php?fid=5](http://ipw2200.sourceforge.net/firmware.php?fid=5)


You must delete (or move) the old ones and copy the new *.fw files of the tarball into /lib/hotplug/firmware/ or /usr/lib/hotplug/firmware/ is the same.
Restart and check with "dmesg|grep ipw" for the new driver (1.0.4). They must be loaded at this time.
With new driver you can put your wifi card in monitor MODE with:

iwconfig eth1 mode monitor

It should not give you error anymore.
You can type an "echo Weeeeee!"
 
7) Download and install svn from:

[http://subversion.tigris.org](http://subversion.tigris.org)

then type:
svn co [http://svn.kismetwireless.net/code/trunk](http://svn.kismetwireless.net/code/trunk) kismet-devel

to get latest devel version of kismet

8) enter into kismet directory and launch  ./configure --sysconfdir=/etc/kismet 

If it give you error, probably you don't have some libraries.
If it give you some error but you have already that libraries, probably you don't have the -dev version of the library (il the library is foo, you need also foo-dev )
For all other software it ask to you, googlish or apt-get (if you use debian)
after follow instruction of kismet (make dep, make, make suidinstall or make install)

9) Edit /etc/kismet/kismet.conf 
My string for the source is:
source=ipw2200,eth1,ATHEROS

10) Run kismet and be happy!


@llergique

---

### Post by MrSandman on 2005-06-26
i can confirm that the newest release of Kismet-2005-06-R1 

wget [http://www.kismetwireless.net/code/kismet-2005-06-R1.tar.gz](http://www.kismetwireless.net/code/kismet-2005-06-R1.tar.gz)

works flawlessly with the ipw2200 and ubuntu

---

### Post by drdeutsch on 2005-06-26
I'm just a linux newbie trying to work my way through this, so I'm a bit confused.

Can I install this on my home directory? Or should I move the Ipw2200 directory to somwehere else on my file system?

also, when I go to "sh remove-old" I get quite a few files, most of which are "ieee80211*" files. Is it safe to remove all of these files or do I only need to remove certain ones? Thanks.


Thanks for answering my newb questions.
drdeutsch

---

### Post by MrSandman on 2005-06-26
[http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623)

this is the tutorial i used to update my drivers. when it gets to the wpa stuff you can stop or go on.

as for installing the linux header use

apt-get install Linux-headers

---

### Post by drdeutsch on 2005-06-26
Thanks, that link helped me out.

I just have one problem now. I've installed everything, but when I go to run it, it doesn't recognize "ipw2200" as a source. This is what it spits out:

> Server options:  none
Client options:  none
Starting server...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'ipw2200' in source 'ipw2200,eth1,ATHEROS'
Waiting for server to start before startuing UI... 

You say it works fine, but mine doesn't recognize my card, even though I've updated the firmware and drivers.

Thanks for your help,
drdeutsch

---

### Post by drdeutsch on 2005-06-27
bump for help.
I've googled and searched quite a few forums and haven't found any answer to this problem yet.

Thanks,
drdeutsch

---

### Post by nybble on 2005-06-27
thanks alot MrSandman

---

