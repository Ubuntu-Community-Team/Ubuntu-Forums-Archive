---
title: "Run Ubuntu inside coLinux"
date: 2005-10-24
forum: General Help
---

### Post by erland on 2005-10-24
I got the question about how I setup Ubuntu to run inside coLinux in [another thread]("http://ubuntuforums.org/showthread.php?p=439713"), so here is a brief description. I am running ubuntu in a dualboot configuration with XP and when booting XP it also starts a coLinux instance using the ubuntu partition. Here are the steps I used to set it up.

1. I installed Ubuntu as normal on a separate partition and configured the computer to dualboot between Ubuntu/XP.

2. I installed coLinux with the Debian with backports image that is available on the coLinux website.

3. Configured coLinux so it could mount the the Ubuntu partition, the trick here is to figure out the correct partition number. The partition number in coLinux seems to be lower that the partition number used when booting the computer with Ubuntu. In my case I had to setup:
<block_device index="1" path="\Device\Harddisk0\Partition5" enabled="true" alias="hda7"/>

4. Boot coLinux with the Debian with backports image and after boot mount the ubuntu partition in my case /dev/hda7

5. To make it possible to boot ubuntu inside coLinux you need to turn of some services autostarted at boot, most of them har hardware related in some way and is not supported inside coLinux. You still want to run these services when not running ubuntu inside colinux. I did this by first creating a /etc/inid.d/colinux script according to [http://wiki.colinux.org/cgi-bin/DualBootSystem]("http://wiki.colinux.org/cgi-bin/DualBootSystem")
This script should of course be created in the /etc/init.d directory on the ubuntu partition and not on the "debian with backports" image.
When this script has been created you also need to edit the default.colinux.xml file so it contains a COLINUX=1 boot-parameter, in my case:
    <bootparams>root=/dev/hda8 COLINUX=1</bootparams>
This script now makes it possible to turn of some autostarted services when starting inside coLinux but still run these services when dualbooting the computer with ubuntu.
You also has to make sure to run this script at boot time by inserting links in the /etc/rcS.d directory.

6. The next step is to turn of services by inserting if-statements inside the service scripts in /etc/init.d (on the ubuntu partition).
if [ -f /var/local/colinux ] ; then
        exit 0
fi

I had to turn off the following services when booting inside coLinux to make it boot, coLinux crashed during boot when any of these services were running:
/etc/init.d/gdm
/etc/init.d/powernowd
/etc/init.d/hotkey-setup
/etc/init.d/pcmcia
/etc/init.d/vbesave

7. Create colinux customized versons of some other files, the colinux script in init.d mentioned above makes it possible to have a colinux-version and a non-colinux version of some different files.
In my case i have special versions of the following files:
/etc/fstab (coLinux mounts the ntfs partitions using smbfs instead of ntfs read-only mounting)
/etc/network/interfaces (I didn't get colinux to work using DHCP so it has hardcoded IP numbers instead)
/etc/gdm/gdm.conf (I am not really sure this is used since gdm can't be started at boot, but I have a special version for coLinux with all [servers] disabled. It may be used when using vnc but I am not sure if it is needed)

It is important to remember to edit correct file when setting up these files this way because the normal files will be overwritten with *-colinux or *-non-colinux versions at each boot. It might be possible to setup symbolic links instead of overwriting the files but I have not tested this.

9. Finally you will have to setup coLinux so it boots using the Ubuntu partition instead of the "debian with backports" image, this is done by setting a boot partition in the default.colinux.xml file, in my case it pointed to /dev/hda8
    <bootparams>root=/dev/hda8 COLINUX=1</bootparams>


10. It should now be possible to either start Ubuntu by selecting it in the dualboot(grub) menu when booting the computer or by starting XP and startup coLinux. Observe that when running inside coLinux the ubuntu kernel is actually not used instead the coLinux kernel is used. This is imporant to think about for example if you need to recompiling kernels and kernel modules.

Finally, don't do the same misstake as I did. As described in [this thread]("http://ubuntuforums.org/showthread.php?p=439713"), I put XP/coLinux into sleep in hibernate mode and then dualbooted into Ubuntu. My ubuntu file system got corrupt at next boot of XP and I decided to do a total reinstallation of Ubuntu.

---

### Post by kingler on 2005-11-17
WOW, great. I also got my Ubuntu native partition working in coLinux! Thanks for the guide. 

it seems the following scripts cannot be run in coLinux
/etc/init.d/gdm
/etc/init.d/powernowd
/etc/init.d/pcmcia
/etc/init.d/vbesave

VNC is set up now, so I can view the GNOME desktop. However I was not able to install FreeNX. It complains about libc6 version. 

Because coLinux is using its own kernel, some programs stoped working, reporting segmentation error. But most of the programs just work fine. 

The speed is pretty good, faster than running in VMWare! I am amazed. :)

---

### Post by vv5 on 2006-05-11
Hello,
  Taking tips, I managed to install dapper (beta2) on a partition and fire
it up from colinux.

however when i install an x application, colinux crashes on the 
preconfiguration stage ( i presume of x-server or somerelated thing).

I was just wondering if there is the soln has already been discovered
by some kind soul, beore I put in my time in it.
--regards
--vv5

UPDATE: I put in a 'exit 0' as first line of all /var/lib/dpkg/info/x11-common.* shell scripts.
The installation went smooth. I've got a xterm from my colinux to Xming.

---

### Post by xymox12 on 2006-07-05
Thanks for this - very useful.

So far I've managed to get Ubuntu command line up but X give lots of errors and won't boot. I think I've got a little confused over 6 - 8 in your tutorial, do maybe someone can help -

1) Do the lines -

/etc/init.d/gdm
/etc/init.d/powernowd
/etc/init.d/hotkey-setup
/etc/init.d/pcmcia
/etc/init.d/vbesave

- go into a file called colinux in /var/local/ along with any other services I may need to stop in the future? If not where do I put these lines?

2) In the script 
SUFFIX=colinux
else
SUFFIX=non-colinux
Does this mean I need to cp all the files (eg /etc/fstab to /etc/fstab-non-colinux (for ubuntu) and /etc/fstab-colinux) and alter them accordingly before starting coliux or booting ubuntu.

Cheers

---

### Post by erland on 2006-07-05
1.
You never modify /var/local/colinux, its just a file that will be created if you boot in colinux. If you boot outside colinux it won't exist.

You add the lines in the scripts in /etc/init.d/*

For example the beginning of my /etc/init.d/vbssave before
```

#!/bin/sh

test -x /usr/sbin/vbetool || exit 0
set -e

```

And after:
```

#!/bin/sh

if [ -f /var/local/colinux ] ; then
        exit 0
fi

test -x /usr/sbin/vbetool || exit 0
set -e

```

2.
As long as you have not made any changes to the scripts you don't have to copy them before restarting. But if you make some changes in the scripts the changes will be lost if you reboot unless you copy the changes to the other files. So you will have to remember to make the changes both in /etc/init.d/*, /etc/init.d/*-colinux and /etc/init.d/*-non-colinux

I have made an updated version of the script that creates soft links with ln -s instead of copying the files, this results in that the changes will not be lost when rebooting. You still have to copy the information to the "other" script, for example if changing someting inside colinux you will have to remember to do the same changes also in non-colinux if you want them when booting outside colinux. The updated script is attached with this post. If you use this update script instead you will have to create the soft links manually the first time, the  script will not overwrite an existing file with a link.

---

### Post by ufoy on 2006-07-22
> **vv5 said:**
> Hello,
  Taking tips, I managed to install dapper (beta2) on a partition and fire
it up from colinux.

however when i install an x application, colinux crashes on the 
preconfiguration stage ( i presume of x-server or somerelated thing).

I was just wondering if there is the soln has already been discovered
by some kind soul, beore I put in my time in it.
--regards
--vv5

UPDATE: I put in a 'exit 0' as first line of all /var/lib/dpkg/info/x11-common.* shell scripts.
The installation went smooth. I've got a xterm from my colinux to Xming.

I am having the same problem with colinux and dapper.  When I am installing anything requiring the x11-common package, colinux will crash.  I have tried following the advice of putting 'exit 0' on all /var/lib/dpkg/info/x11-common.* scripts, but unfortunately, I do not have these scripts.  Can anyone show me how to stop the x11-common installation from launching a X session so that colinux won't crash?

Thanks,
ufoy

---

### Post by mirak63 on 2006-07-22
> **kingler said:**
> VNC is set up now, so I can view the GNOME desktop. However I was not able to install FreeNX. It complains about libc6 version. 


You can setup gdm so it can acept remote login with a distant X server.
So you just have to install an X server on windows side. you can use Cygwin for that.
Then from cygwin command line you can do X -query remote_colinux_ip_adress
That wil be way smoother than vnc, and since it's local freenx isn't really  usefull.[/QUOTE]

> Because coLinux is using its own kernel, some programs stoped working, reporting segmentation error. But most of the programs just work fine. 


probably you can patch the ubuntu kernel with colinux patches, but that's probably not easy :mrgreen: 

> The speed is pretty good, faster than running in VMWare! I am amazed. :)

it's fast because there is no hardware emulation at all :o

---

### Post by vv5 on 2006-09-06
> **ufoy said:**
> I am having the same problem with colinux and dapper.  When I am installing anything requiring the x11-common package, colinux will crash.  I have tried following the advice of putting 'exit 0' on all /var/lib/dpkg/info/x11-common.* scripts, but unfortunately, I do not have these scripts.  Can anyone show me how to stop the x11-common installation from launching a X session so that colinux won't crash?

Thanks,
ufoy


please add exit 1 as second line in /usr/sbin/laptop-detect
after aptitude install laptop-detect.
then do aptitude install x11-common, and you should be fine.

---

### Post by vv5 on 2006-09-06
I put up some rough notes on 
[http://wiki.colinux.org/wiki/Dapper](http://wiki.colinux.org/wiki/Dapper)

---

### Post by Dolijr on 2006-10-25
Sorry completely New to linux.
When you say "mount the ubuntu partition in my case /dev/hda7"
I tried just mount /dev/hda7 and it tells me that I can not do that... How do I mount /dev/hda7 ??? Thanks

---

### Post by alh84001 on 2006-11-21
I've done it. I got my Ubuntu running in Windows.
Well almost :)
There is a strange problem. I can start Ubuntu once in my windows session, but after that if I start it coLinux crashes. Strangely enough when I restart Windows (it doesn't work with log out) I can then again normally start Ubuntu.
coLinux seems to crash right after it displays "setting up hp printers" during boot (or sth like that) and I think it does that fine. After that line normally there would be a line similar to "Starting OpenBSD shell".
Anyone have any ideas?

---

### Post by cseg on 2007-01-28
I've just visited [http://goodbye-microsoft.com](http://goodbye-microsoft.com) which is a site which allows you to install Debian over the web inside of Windows (dual boot) with just a single click.

That site has a reference to the Ubuntu page ([https://wiki.ubuntu.com/install.exe](https://wiki.ubuntu.com/install.exe)) that gave them the idea.  The Ubuntu idea is a little different than the Debian implementation (it uses bittorrent among other differences).  But I find the idea of installing Linux with just a single web click an awesome idea.

The problem, of course, is that you are left with a dual boot system.

Anyone up for enhancing this so that with a single click, you can get a coLinux/Ubuntu system up?

:)

---

### Post by motscousus on 2007-04-11
i found that feisty would run out-of-the-box with colinux 0.8 snapshot.
[http://colinux.org/snapshots/](http://colinux.org/snapshots/)

i however disabled all hardware related daemons as well as gdm graphical greeter.
(some service must be disabled by tweaking scripts in /etc/init.d/, some others in the /etc/d-bus/event.d/ 

henri

---

### Post by andrewroth on 2007-05-20
Hey guys, check out my post at [http://ubuntuforums.org/showthread.php?p=2687214#post2687214](http://ubuntuforums.org/showthread.php?p=2687214#post2687214)

---

### Post by ryanwsx on 2007-09-17
Very2 interesting, well, sorry to ask but can we use ubuntu desktop environment too ?
i mean, i use GNOME ubuntu feisty in VirtualBox, but my machine only have 512Mb and windows is still needed for my work.

My Ubuntu VirtualBox only using 160MB memory and when i use it, i cant run WIndows APP anymore without slowing down the entire system.

Well, if Colinux can replace VirtualBox, i'll be very2 happy.

And how to load my ubuntu in colinux without reinstalling. I think must use a converter that convert .vdi image from VirtualBox to a image that supported by colinux. I have googled but no luck so far.

---

### Post by bodhi.zazen on 2007-09-17
> **ryanwsx said:**
> Very2 interesting, well, sorry to ask but can we use ubuntu desktop environment too ?
i mean, i use GNOME ubuntu feisty in VirtualBox, but my machine only have 512Mb and windows is still needed for my work.

My Ubuntu VirtualBox only using 160MB memory and when i use it, i cant run WIndows APP anymore without slowing down the entire system.

Well, if Colinux can replace VirtualBox, i'll be very2 happy.

And how to load my ubuntu in colinux without reinstalling. I think must use a converter that convert .vdi image from VirtualBox to a image that supported by colinux. I have googled but no luck so far.

Colinux is very cool. It takes a little tweakig to get up and running, but it ahs become a lot nicer.

Your limiting factor here, however, is RAM (each OS still needs RAM). If at all possible consider upgrading your RAM, hopefully it is not too expensive to do so ...

---

### Post by erland on 2007-09-18
> **ryanwsx said:**
> Very2 interesting, well, sorry to ask but can we use ubuntu desktop environment too ?
i mean, i use GNOME ubuntu feisty in VirtualBox, but my machine only have 512Mb and windows is still needed for my work.

My Ubuntu VirtualBox only using 160MB memory and when i use it, i cant run WIndows APP anymore without slowing down the entire system.

Well, if Colinux can replace VirtualBox, i'll be very2 happy.

And how to load my ubuntu in colinux without reinstalling. I think must use a converter that convert .vdi image from VirtualBox to a image that supported by colinux. I have googled but no luck so far.
Yes, you can use GNOME when you are running ubuntu in coLinux. Unless something has changed since I used coLinux last time, you do it by installing ubuntu inside coLinux and besides this you also install an X server on the windows machine. As X server I used cygwin but there are also other X servers available.

As already noted though, this won't solve your problem. Running two graphical operating systems with totally 512MB is always going to be slow, coLinux doesn't make this any better. coLinux might be a bit better if you like to run non graphical applications most of the time and just in some specific situations need to startup the graphical X interface.

---

### Post by bodhi.zazen on 2007-09-18
> **erland said:**
> Yes, you can use GNOME when you are running ubuntu in coLinux. Unless something has changed since I used coLinux last time, you do it by installing ubuntu inside coLinux and besides this you also install an X server on the windows machine. As X server I used cygwin but there are also other X servers available.

+1 on cygwin.

FYI, you do NOT need a X server on Windows if you use a VNC connection. Install a vncserver (tightvnc, freenx) on the Ubutnu guest and use a vnc client on windows to connect (Tightvnc, openvnc, freenx, etc), tunneled over ssh if you prefer.

VNC is faster then a tunneled ssh desktop.

---

### Post by Falkon on 2007-10-22
Is there a way to use coLinux to run Ubuntu without having a partiton?  I was under the impression that coLinux could hold all the data on one windows partition and allow you to run linux from there, but maybe I just misunderstood.

---

### Post by erland on 2007-10-23
> **Falkon said:**
> Is there a way to use coLinux to run Ubuntu without having a partiton?  I was under the impression that coLinux could hold all the data on one windows partition and allow you to run linux from there, but maybe I just misunderstood.
I think the problem is the installation, when you have a working ubuntu partition that runs in coLinux it should be possible to move that into a image that can be placed onto the Windows file system.

The problem is to get there without having a separate partition. I don't think you can install ubuntu from inside coLinux, the reason is that it needs some patching as mentioned earlier before it can run inside coLinux. The result is that someone probably has to do the installation and patching and then make an image available for download. 

An alternative, as already mentioned, would be that you did this yourself by creating a separate partition and perform the installation and patching and then create an image of the partition and put it on the Windows file system. After you have put the image on the Windows file system you don't need the extra partition any more.

---

### Post by daflame on 2007-12-04
My question is, why not setup a connection into the coLinux with NX.  Would that not solve all the problems of running an X server on windows and there is a great guide that is setup here thanks to the FreeNX community's help:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

---

### Post by Laibcoms on 2008-05-01
Question, this method also allows, for example, cross-clipboard usage by XP and Ubuntu-on-coLinux right, similar to what andLinux can do?  (andLinux only offers KDE, I prefer GNOME :p so going to use your guide)

Thanks in advance for the info.  :D

---

