---
title: "Not able to hear sound from my Ubuntu to Samsung TV"
date: 2017-11-04
forum: General Help
---

### Post by magneto2 on 2017-11-04
Hi guys,

I am really struggling because everything I tried online it is not working so I am now here posting this message and hoping someone can really help.

I am connecting through HDMI cable my laptop dv9000 (I know it is pretty old) with a Samsung smart tv and I am not able to hear the sound.
The screen is there, all good. But no sound coming out from TV.

In the sound settings strangely I do not have HDMI option but only S/PDIF digital output (and the standard build in speakers option that it is working, that means I can hear sound coming out from my laptop while the TV is connected)

Well I ccould use the laptop for the sound and the TV for the image but it is not ideal you know.

Please help.

I can post whatever you need from the terminal to help the troubleshooting.

Thanks in advance.

Mario

---

### Post by #&amp;thj^% on 2017-11-04
Bad or Wrong cable comes to mind first off. Or even a bad port/HDMI.
What sound setting are you referring to?
Pulse Audio Tabs Configuration

---

### Post by magneto2 on 2017-11-04
cable is OK because on another ubuntu coputer (old too) is working great. and actually I do not have S/PDIF but HDMI.

I am speaking about when you look for "sound" on ubuntu and you have the sound settings. You can also access from the volume symbol on top right on my screen if I double click on it.

Thanks.

I do not know what is that screenshot you are showing me :(

Found it:

[IMG][[img]https://preview.ibb.co/gO0VDG/Screenshot_from_2017_11_04_19_35_46.png[/img]](https://ibb.co/fy8vfw)[/IMG]

I can actually see THE BAR MOVING!!! but no sound out of tv..crazy

---

### Post by #&amp;thj^% on 2017-11-04
Oh sorry about that, I could have been just a bit more clear.
What dose this give from the terminal:
```
apt policy pavucontrol
```
Paste back the return please.

---

### Post by magneto2 on 2017-11-04
pavucontrol:
  Installed: 3.0-3build1
  Candidate: 3.0-3build1
  Version table:
 *** 3.0-3build1 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by #&amp;thj^% on 2017-11-04
Ok Great. Now go to Multimedia in your menu>>and open Pulse Audio Volume, and you should see that tab on the right hand side at the top Tabs.
If you can take a screenshot of that and Attach it in you next reply.

---

### Post by magneto2 on 2017-11-04
[URL="https://ibb.co/cdRb3G"][IMG]https://preview.ibb.co/f7mb3G/Screenshot_from_2017_11_04_20_28_06.png[/IMG]

[/URL]

---

### Post by magneto2 on 2017-11-04
In case you were thinking to ask what other options are in that drop menu:

analog output (I can hear sound from laptop)
the one selected
digital output
analog input

---

### Post by #&amp;thj^% on 2017-11-04
Yuck! not a good sign.
Looks like that lappy has a bad HDMI/port.
If you would do one more thing for me>>install inxi and give me the return from this:
To install 
```
sudo apt install inxi 

```
And paste back return from this:
```
inxi -A
```
Mine looks like this
```
Audio:     Card-1 NVIDIA GF114 HDMI Audio Controller driver: snd_hda_intel
           Card-2 Intel Sunrise Point-H HD Audio driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.13.11-1-ARCH

```

---

### Post by magneto2 on 2017-11-04
not able to install:

Unpacking libsigsegv2:amd64 (2.10-4) over (2.10-4) ...
dpkg: unrecoverable fatal error, aborting:
 fork failed: Cannot allocate memory
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by #&amp;thj^% on 2017-11-04
The Plot Thickens. ;)
Now we are heading into overtime>>:lolflag:

Can you post back the return from both of these, one at time.
```
free
```
and now:
```
df -h
```

---

### Post by magneto2 on 2017-11-04
total        used        free      shared  buff/cache   available
Mem:        2047200     1532620      103304       55080      411276      279068
Swap:             0           0           0

---

### Post by magneto2 on 2017-11-04
Filesystem              Size  Used Avail Use% Mounted on
udev                    980M     0  980M   0% /dev
tmpfs                   200M  6.3M  194M   4% /run
/dev/sdb6               108G   39G   65G  38% /
tmpfs                  1000M   24M  977M   3% /dev/shm
tmpfs                   5.0M  4.0K  5.0M   1% /run/lock
tmpfs                  1000M     0 1000M   0% /sys/fs/cgroup
cgmfs                   100K     0  100K   0% /run/cgmanager/fs
tmpfs                   200M   68K  200M   1% /run/user/1000
/home/magneto/.Private  108G   39G   65G  38% /home/magneto

---

### Post by #&amp;thj^% on 2017-11-04
Ok 
Welp looks like we go some extra steps then:
```
sudo apt update && sudo apt upgrade && sudo apt autoremove 
```
Show any errors given from the above.

---

### Post by magneto2 on 2017-11-04
I posted both already

---

### Post by #&amp;thj^% on 2017-11-04
Yep seen that after I posted >> See my above post#14

---

### Post by magneto2 on 2017-11-04
Hit:1 [http://ppa.launchpad.net/openjdk-r/ppa/ubuntu](http://ppa.launchpad.net/openjdk-r/ppa/ubuntu) xenial InRelease
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease                     
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Hit:4 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial InRelease        
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Hit:7 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Get:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [652 kB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [616 kB]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [60.2 kB]
Get:11 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [308 kB]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [62.6 kB]
Get:13 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [213 kB]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [51.4 kB]
Get:15 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [543 kB]
Get:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [85.1 kB]
Get:17 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [517 kB]
Get:18 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [174 kB]
Get:19 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [245 kB]
Get:20 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [5,888 B]
Get:21 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,324 B]
Get:22 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [4,588 B]
Fetched 3,847 kB in 4s (935 kB/s)                               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
6 packages can be upgraded. Run 'apt list --upgradable' to see them.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by #&amp;thj^% on 2017-11-04
Ok now we run
```
sudo dpkg --configure -a
```
Again post back any errors

---

### Post by magneto2 on 2017-11-04
magneto@magneto-Pavilion-dv9000-GH766EA-ABZ:~$ sudo dpkg --configure -a
[sudo] password for magneto:
magneto@magneto-Pavilion-dv9000-GH766EA-ABZ:~$ sudo dpkg --configure -a
magneto@magneto-Pavilion-dv9000-GH766EA-ABZ:~$ 





nothing happened

---

### Post by #&amp;thj^% on 2017-11-04
Ok now we see if the needed fix worked:
```
sudo apt upgrade
```

---

### Post by magneto2 on 2017-11-04
```
magneto@magneto-Pavilion-dv9000-GH766EA-ABZ:~$ sudo apt upgrade
[sudo] password for magneto: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  comerr-dev g++-4.8 gcc-5-base:i386 gvfs:i386 gvfs-libs:i386
  javascript-common krb5-multidev libamd2.3.1 libart-2.0-2:i386
  libasound2:i386 libatk1.0-0:i386 libavahi-client-dev libavahi-client3:i386
  libavahi-common-dev libavahi-common3:i386 libavahi-glib1:i386 libavcodec54
  libavformat54 libavutil52 libbonobo2-0:i386 libbonoboui2-0:i386
  libboost-program-options1.54.0 libboost-program-options1.55.0
  libboost-python1.55.0 libboost-regex1.54.0 libboost-regex1.55.0
  libboost-signals1.54.0 libboost-signals1.55.0 libboost-system1.55.0
  libcairo2:i386 libcamd2.3.1 libcanberra0:i386 libccolamd2.8.0
  libcgmanager0:i386 libcholmod2.1.2 libcoin80v5 libcups2:i386 libdatrie1:i386
  libdbus-1-3:i386 libdbus-glib-1-2:i386 libexif-dev libfontconfig1:i386
  libfreeimage3 libfreetype6:i386 libgail18:i386 libgck-1-0:i386
  libgconf-2-4:i386 libgcr-base-3-1:i386 libgcrypt11:i386 libgcrypt11-dev
  libgcrypt20-dev libgdk-pixbuf2.0-0:i386 libgegl-0.2-0 libgl2ps0
  libglade2-0:i386 libglib2.0-0:i386 libgmp-dev libgmp10:i386 libgmpxx4ldbl
  libgnome-2-0:i386 libgnome-keyring0:i386 libgnome2-0:i386
  libgnomecanvas2-0:i386 libgnomeui-0:i386 libgnomevfs2-0:i386 libgnutls-dev
  libgnutls26:i386 libgnutls30:i386 libgnutlsxx27 libgnutlsxx28
  libgpg-error-dev libgphoto2-dev libgraphite2-3:i386 libgssapi-krb5-2:i386
  libgssrpc4 libgtk2.0-0:i386 libharfbuzz0b:i386 libhogweed4:i386 libice6:i386
  libicu55:i386 libidl-2-0 libidl-2-0:i386 libidl-common libidn11:i386
  libidn11-dev libieee1284-3-dev libilmbase6 libjasper1:i386
  libjavascriptcoregtk-1.0-0 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386
  libjs-jquery libjs-jquery-ui libjs-sphinxdoc libjs-underscore libjxr0
  libk5crypto3:i386 libkadm5clnt-mit9 libkadm5srv-mit9 libkdb5-8
  libkeyutils1:i386 libkrb5-3:i386 libkrb5-dev libkrb5support0:i386 liblcms1
  libllvm3.8 libltdl7:i386 libmircommon5 libnettle6:i386 libnglib-4.9.13
  libnih-dbus1:i386 libnih1:i386 liboce-foundation10 liboce-foundation8
  liboce-modeling10 liboce-modeling8 liboce-ocaf-lite10 liboce-ocaf-lite8
  liboce-ocaf10 liboce-ocaf8 liboce-visualization10 liboce-visualization8
  libogg0:i386 libopenexr6 libopenjp2-7 libopenjpeg2 liborbit-2-0:i386
  liborbit2 liborbit2:i386 libp11-kit-dev libp11-kit0:i386 libpango-1.0-0:i386
  libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386 libpixman-1-0:i386
  libpng12-0:i386 libpopt0:i386 libpyside1.2 libqtwebkit-dev
  libsecret-1-0:i386 libshiboken1.2v5 libsigsegv2 libsm6:i386 libsoqt4-20
  libspnav0 libstdc++-4.8-dev libstdc++6:i386 libtasn1-6:i386 libtasn1-6-dev
  libtasn1-doc libtdb1:i386 libthai0:i386 libtiff5:i386 libumfpack5.6.2
  libv4l-dev libv4l2rds0 libvorbis0a:i386 libvorbisfile3:i386
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libx11-6:i386 libx264-142
  libxau6:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb1:i386
  libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386
  libxerces-c3.1 libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386
  libxml2:i386 libxrandr2:i386 libxrender1:i386 libzipios++0c2a
  linux-headers-3.13.0-37 linux-headers-3.13.0-37-generic
  linux-headers-3.13.0-43 linux-headers-3.13.0-43-generic
  linux-headers-3.13.0-54 linux-headers-3.13.0-54-generic
  linux-headers-3.13.0-57 linux-headers-3.13.0-57-generic
  linux-headers-4.4.0-51 linux-headers-4.4.0-51-generic linux-headers-4.4.0-57
  linux-headers-4.4.0-57-generic linux-headers-4.4.0-66
  linux-headers-4.4.0-66-generic linux-headers-4.4.0-93
  linux-headers-4.4.0-93-generic linux-headers-4.4.0-96
  linux-headers-4.4.0-96-generic linux-image-3.13.0-37-generic
  linux-image-3.13.0-43-generic linux-image-3.13.0-54-generic
  linux-image-3.13.0-57-generic linux-image-4.4.0-51-generic
  linux-image-4.4.0-57-generic linux-image-4.4.0-66-generic
  linux-image-4.4.0-93-generic linux-image-4.4.0-96-generic
  linux-image-extra-3.13.0-37-generic linux-image-extra-3.13.0-43-generic
  linux-image-extra-3.13.0-54-generic linux-image-extra-3.13.0-57-generic
  linux-image-extra-4.4.0-51-generic linux-image-extra-4.4.0-57-generic
  linux-image-extra-4.4.0-66-generic linux-image-extra-4.4.0-93-generic
  linux-image-extra-4.4.0-96-generic nettle-dev python-collada python-cycler
  python-dateutil python-matplotlib python-matplotlib-data python-numpy
  python-pivy python-ply python-pyparsing python-pyside.qtcore
  python-pyside.qtgui python-pyside.qtsvg python-pyside.qtuitools
  python-pyside.qtxml python-qt4-gl python-support python-tz snap-confine
  ubuntu-core-launcher
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  evince evince-common iproute2 libevdocument3-4 libevview3-3 libsigsegv2
6 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/1,438 kB of archives.
After this operation, 62.5 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 996045 files and directories currently installed.)
Preparing to unpack .../libsigsegv2_2.10-4_amd64.deb ...
Unpacking libsigsegv2:amd64 (2.10-4) over (2.10-4) ...
Preparing to unpack .../iproute2_4.3.0-1ubuntu3.16.04.2_amd64.deb ...
Unpacking iproute2 (4.3.0-1ubuntu3.16.04.2) over (4.3.0-1ubuntu3.16.04.1) ...
Preparing to unpack .../evince_3.18.2-1ubuntu4.2_amd64.deb ...
Unpacking evince (3.18.2-1ubuntu4.2) over (3.18.2-1ubuntu4.1) ...
Preparing to unpack .../libevdocument3-4_3.18.2-1ubuntu4.2_amd64.deb ...
Unpacking libevdocument3-4:amd64 (3.18.2-1ubuntu4.2) over (3.18.2-1ubuntu4.1) ...
Preparing to unpack .../libevview3-3_3.18.2-1ubuntu4.2_amd64.deb ...
Unpacking libevview3-3:amd64 (3.18.2-1ubuntu4.2) over (3.18.2-1ubuntu4.1) ...
Preparing to unpack .../evince-common_3.18.2-1ubuntu4.2_all.deb ...
Unpacking evince-common (3.18.2-1ubuntu4.2) over (3.18.2-1ubuntu4.1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Processing triggers for libglib2.0-0:i386 (2.48.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.48.2-0ubuntu1) ...
Setting up libsigsegv2:amd64 (2.10-4) ...
Setting up iproute2 (4.3.0-1ubuntu3.16.04.2) ...
Setting up libevdocument3-4:amd64 (3.18.2-1ubuntu4.2) ...
Setting up libevview3-3:amd64 (3.18.2-1ubuntu4.2) ...
Setting up evince-common (3.18.2-1ubuntu4.2) ...
Setting up evince (3.18.2-1ubuntu4.2) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
magneto@magneto-Pavilion-dv9000-GH766EA-ABZ:~$ 
```




And now? Any hope?

---

### Post by #&amp;thj^% on 2017-11-04
Please don't take this wrong>>Please use **code tags for Long outputs** easier on the old eyes. :)  and preserves the format.
Now we try again with:
```
sudo apt install inxi
```
And return the output from:
```
inxi -A
```

---

### Post by magneto2 on 2017-11-04
```
magneto@magneto-Pavilion-dv9000-GH766EA-ABZ:~$ inxi -A
Audio:     Card NVIDIA MCP51 High Definition Audio driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.4.0-98-generic
magneto@magneto-Pavilion-dv9000-GH766EA-ABZ:~$ 

```

---

### Post by magneto2 on 2017-11-04
```
magneto@magneto-Pavilion-dv9000-GH766EA-ABZ:~$ inxi -c 5 -b
System:    Host: magneto-Pavilion-dv9000-GH766EA-ABZ Kernel: 4.4.0-98-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   System: Hewlett-Packard (portable) product: Pavilion dv9000 (GH766EA#ABZ) v: Rev 1
           Mobo: Quanta model: 30B9 v: 65.2C
           Bios: Hewlett-Packard v: F.41 date: 11/26/2008
CPU:       Dual core AMD Turion 64 X2 Mobile TL-56 (-MCP-)
           speed/max: 800/1800 MHz
Graphics:  Card: NVIDIA G73M [GeForce Go 7600]
           Display Server: X.Org 1.18.4 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1152x864@59.96hz, 1152x864@59.97hz
           GLX Renderer: Gallium 0.4 on NV4B GLX Version: 2.1 Mesa 17.0.7
Network:   Card-1: NVIDIA MCP51 Ethernet Controller driver: forcedeth
           Card-2: Broadcom BCM4311 802.11a/b/g driver: b43-pci-bridge
Drives:    HDD Total Size: 240.1GB (17.1% used)
Info:      Processes: 200 Uptime: 38 min Memory: 1191.9/1999.2MB
           Client: Shell (bash) inxi: 2.2.35 
magneto@magneto-Pavilion-dv9000-GH766EA-ABZ:~$ 

```

---

### Post by magneto2 on 2017-11-04
I learned how to use inxi:D

Just to give you more info...;)

---

### Post by magneto2 on 2017-11-04
I suppose the overtime is finished (I can see you are offline now)..If you can help me more will be really greatfull...I might install some drivers? It seems I do not have the proper card there...

I will check the thread tomorrow afternoon again. Thanks for all. I hope my computer is not too messy:(:confused:

---

### Post by #&amp;thj^% on 2017-11-04
> **magneto2 said:**
> I learned how to use inxi:D

Just to give you more info...;)
Yay so it wasn't a total waste of time>:) inxi is a great tool as you learn more about it.:)
I'm still thinking you have a bad hdmi port though. :(
I remember mine "Pavilion-dv9000" working with the hdmi port HDMI audio.
Do you have the legacy NVIDIA Driver installed? (Maybe give that a try)

---

### Post by jeremy31 on 2017-11-04
I think I would try a new HDMI cable.  I had issues with sound to my TV from a satellite receiver until I replaced my cable.

---

### Post by #&amp;thj^% on 2017-11-04
> **jeremy31 said:**
> I think I would try a new HDMI cable.  I had issues with sound to my TV from a satellite receiver until I replaced my cable.

+1 He says the same cable works with another Ubuntu install?
> cable is OK because on another ubuntu coputer (old too) is working great. and actually I do not have S/PDIF but HDMI.

@ magneto2 you have a lot of UN-needed packages now...best to tidy up a bit with:
```
sudo apt autoremove
```
I'll checkin tomorrow to see how you are getting along.
Cheers

---

### Post by magneto2 on 2017-11-05
Good morning guys, so kind of you!

For the cable: It was working on my wife laptop Acer inspire old 2009 (that we binned because the motherboard was gone. That is why I am trying to make it works on mine!) with Ubuntu 14.04. I have Ubuntu 16.04 but was not working with 14.04 either.
Shall we leave the option of buying another cable at the end because does not seem that is the issue?

For the UN-needed package, I will do.

For the legacy NVIDIA Driver installed I am not sure I have...could I have some code to check and install in case please?

Thanks a lot. I catch you later

---

### Post by #&amp;thj^% on 2017-11-05
Here is a pretty good write up to fixing No sound through your HDMI.

[https://itsfoss.com/how-to-fix-no-sound-through-hdmi-in-external-monitor-in-ubuntu/](https://itsfoss.com/how-to-fix-no-sound-through-hdmi-in-external-monitor-in-ubuntu/)

**Note that you must be connected to an external monitor through a HDMI cable to see HDMI output option.**

Also "to" check if you are using the Nvidia Driver.
For 14.04
```
apt-cache policy nvidia-304
```
For 16.04
```
apt policy nvidia-304
```
Or you can also use this:
```
lsmod | grep nvidia
lsmod | grep nouveau

```
If you choose to install the Nvidia binary blob.
Use this command to give your options for your card >>Under "Additional Drivers" 
```
software-properties-gtk
```
Don't forget to apply the changes and reboot to use the newly installed driver

---

### Post by magneto2 on 2017-11-13
> **1fallen said:**
>  ... 

Dear 1fallen, please accept my apologies but I was really busy. I will do as per your last post (I already follow all the previous indications) and come back to you/the community on this matter.

Really thanks mate

M.[[COLOR=#000000][/COLOR]]("https://ubuntuforums.org/member.php?u=2040855")

---

