---
title: "Nvidia GeForce GTX 750 Ti grahpics card crashes"
date: 2015-02-15
forum: General Help
---

### Post by chris137 on 2015-02-15
Hi,
I got my new graphics card about three weeks ago.
Sometimes it just crashes - no idea why, can't reproduce it.
Last time it happened about an hour ago I was working on Firefox so nothing big.
I am using three monitors.
lspci -nnk gives me this:

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] [10de:1380] (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device [1043:84bb]
    Kernel driver in use: nvidia

I am using lightdm. Restarting it has no effect on my screens. It just freezes like that (picture attached below).
Everything else still works (e.g. ssh-access or music playing).

Not sure if it might be part of the problem but when running nvidia-settings via terminal I get this message:
** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no

As far as I understood what nvidia-prime is I did neither install it nor did I want to use it.

The important question here is: Hardware-problem or software-problem?

As usual I probably forgot some important information. If so please just ask for it.

Here is a picture of what it looks like on two screens: (no idea how to resize..)
[IMG]http://pic.dnsts.de/q0Slxg.png[/IMG]

---

### Post by efflandt on 2015-02-15
Which nvidia drivers are you using? The old 304 version initial nvidia-current in 14.04.1 (judging from logs) did not even support my GTX 750 Ti with the new Maxwell chip. Although, apparently an updated 304 version in a small backup 12.04 system appeared to work. It would be better to install either **nvidia-331** or **nvidia-331-updates** packages. But I wanted to play around with overclocking (which requires 337 or newer), so I added xorg-edgers ppa and installed **nvidia-346**.

I have a MSI Twin Frozr GTX 750 Ti used on a single 1080p HDTV and have had no problems with that once I had nvidia-331 or newer.

---

### Post by chris137 on 2015-02-16
I am using version 331.20 on 14.04 and there is no need for overclocking.

---

### Post by chris137 on 2015-02-17
Any ideas?
If it is a hardware-issue I'd want to return the card ASAP.

---

### Post by Bashing-om on 2015-02-17
chris137; Hi !

The 750ti is still 'new' and drivers are not available in the software repository.
Several PPAs offer support;
See:
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
[http://ubuntuforums.org/showthread.php?t=2257506](http://ubuntuforums.org/showthread.php?t=2257506)
[http://ubuntuforums.org/showthread.php?t=2250468](http://ubuntuforums.org/showthread.php?t=2250468)

Ya might purge and (RE-)install the Nvidia proprietary driver, see what results.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-02-18
Thanks.
I did not get to read through those threads.
Today it happened again so I checked once again an issue I had before.
The case does not really work with this card. I had to bend it a little so the HDMI-port was usable at all.
I just realized that the cable did not even fit correctly.
Now it did some more bending and hope that this was the problem.
Anyway I will reading through those threads you posted above.

Is it even possible that a lose cable caused this?

---

### Post by Bashing-om on 2015-02-18
chris137; Hey ... hey;

> 
Is it even possible that a lose cable caused this?

Most assuredly ! And bending a card is not a good thing either; what happens is a broke 'printed circuit' !

But if it works, 
[INDENT][INDENT]more power to us
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-02-18
Surely I would not try bending a card :D
What I bent was just some metal around the port.
I'll see if that really was the problem when there won't be any problems :D

Thanks for your help though.

---

### Post by chris137 on 2015-02-20
Unfortunately I got the same error today.
I now tried the first link you provided and hope it helps.
Meanwhile different ideas?

Edit: Well these were fun 30 minutes.
First it didn't work, then it didn't work at all.
Probably caused by just installing the new driver without removing the old one.
Kind of thought the installer would to it itself.
I think I managed it now.
Let's see if it helps.

---

### Post by Bashing-om on 2015-02-21
chris137; Welp'

As you have found out, installing the proprietary driver will not remove the old one. You must manually remove the other driver prior to installing another proprietary driver.
So, where do we stand ?
More than 1 driver presently installed ?
```

dpkg -l | grep nvidia

```

What driver built (if any ) ?
```

sudo lshw -C display
cat /var/log/Xorg.0.log

```

[INDENT][INDENT]a tale is told ?
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-02-21
Yeah, noticed that after nothing worked after a reboot.
I then removed the old driver with apt-get remove --purge nvidia-* and then installed the new one using these steps:
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
Sadly it now flickers every now and then but just at one spot and it stops after 1-2seconds.
Annoying but I will stick to this driver for a few days just to test if it freezes again.
dpkg -l | grep nvidia 
gives no output at all.. weird.

sudo lshw -C display
  *-display               
       Beschreibung: VGA compatible controller
       Produkt: GM107 [GeForce GTX 750 Ti]
       Hersteller: NVIDIA Corporation
       Physische ID: 0
       Bus-Informationen: pci@0000:01:00.0
       Version: a2
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress vga_controller bus_master cap_list rom
       Konfiguration: driver=nvidia latency=0
       Ressourcen: irq:47 memory:fa000000-faffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(Größe=128) memory:fb000000-fb07ffff

/var/log/Xorg.0.log has over 600 lines and smh I'm too dumb to copy it all. Need to leave soon anyway.

---

### Post by Bashing-om on 2015-02-21
chris137; Hummm ..


"dpkg -l | grep nvidia"  - I do not know ! - but maybe, as the Nvidia driver was installed from PPA, the package manager (dpkg) is unaware of it's existence ?

Let's do look at the Xorg.0.log file. An easy way to relay that file:
```

sudo apt-get install pastebinit
cat /var/log/Xorg.0.log | pastebinit

```
--testing presently yields :
> 
sysop@1404mini:~$ cat /var/log/Xorg.0.log | pastebinit
Failed to contact the server: [Errno socket error] timed out
sysop@1404mini:~$

If you too have problems. wait a while and try again.
The expected output is a URL .
Pass that resulting URL back here and we take a read of the file.

[INDENT][INDENT]maybe we learn something to help
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-02-22
Well that is awesome.
Had pastebin in mind for a second but I did not know there was a package!
[http://paste.ubuntu.com/10355830/](http://paste.ubuntu.com/10355830/)
Looked through the file before posting but it did not really help me.
Maybe someone knows what to look for.

---

### Post by Bashing-om on 2015-02-22
chris137; Welp; Not optimum ;

To say the least.

The Nvidia driver is built and loaded :
> 
12.909] (II) NVIDIA dlloader X Driver  346.35  Sat Jan 10 20:32:18 PST 2015
13.658] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 750 Ti (GM107-A) at PCI:1:0:0 (GPU-0)

But ! It blows my knowledge away that:
> 
13.662] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 750 Ti at PCI:1:0:0

the display is found, BUT, BUT .. seems like a resolution can not be determined ?
> 
13.664] (WW) NVIDIA(GPU-0): The EDID for Acer G246HYL (DFP-1) contradicts itself: mode
[    13.664] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    13.664] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-75.000 Hz) would exclude
[    13.664] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[    13.664] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".

many times over seeking for a resolution, and not finding one !

I must admit this is beyond my experience, I can not imagine what causes this condition - perhaps a bad cable between the graphics card and the monitor ?? I honestly do not know. Others now will have to advise .

[INDENT][INDENT]if I knew everything
[INDENT][INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris137 on 2015-02-22
So after reading through similar issues I am starting to think the EDID-errors are not relevant to my issue.
As far as I understood somewhere it gets the information that 56-75Hz is supported and somewhere else that also 50Hz would be supported.
Since I am using 60Hz it does not matter what is right... I guess.

However it does not really help me.
If I am right there is a different issue and I can't locate it.

---

### Post by Ruben_van_Smirren on 2015-02-24
what you see is called "artifacts" you can't do anything about it since this is a hardware failure. Your GPU memory is broken. Return the GPU to the manufacturer!

---

### Post by chris137 on 2015-02-25
Trusting Ruben I returned my old card today since it seemed likely to me he was right.
I also ordered a new one which just arrived.
Sadly I already notived that there still is flickering.
This is my Xorg.0.log which - at first view - is pretty much the same as before.
[http://paste.ubuntu.com/10412378/](http://paste.ubuntu.com/10412378/)

'dpkg -l | grep nvidia' still has no output and the one of 'sudo lshw -C display' did not change (luckily)

---

### Post by Bashing-om on 2015-02-25
chris137; Shucks;

Good I guess that it is not a hardware problem ( cable or connection ?), bad that I have no other idea of  where to look for the problem .

But we can continue to poke at it and see what we can learn.

I would expect 'dpkg' to see the Nvidia package(s) .
What returns ?
```

dpkg -l | grep -i nvidia
sudo find / -name "NVIDIA-Linux-*"
sudo find / -name "nvidia*"

```

a shot in the dark:
First move current one to xorg.conf.old; 
```

sudo mv /etc/X11/Xorg.conf /etc/X11/Xorg.conf.old
sudo nvidia-xconfig

```
to regenerate the config file.
Now restart so that the Nvidia driver can take effect.

Not that I know a lot, or would recognize a problem - others might and at this time will be a good idea to look at that config file:
```

cat /etc/X11/Xorg.conf

```

When all said and done from the above,
What now does the system report ?
```

nvidia-settings -h | head -2

```

[INDENT][INDENT]I do not know
[INDENT][INDENT][INDENT]I would like to learn
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris137 on 2015-02-25
-i is never a bad idea:
dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                               0.7-2ubuntu1                                        amd64        Interface for toggling the power on nVidia Optimus video cards
ii  libcuda1-331-updates                                        331.113-0ubuntu0.0.4                                amd64        NVIDIA CUDA runtime library

sudo find / -name "NVIDIA-Linux-*" only returns my manually downloaded driver at 
/home/chris/NVIDIA-Linux-x86_64-346.35.run

sudo find / -name "nvidia*"
[http://paste.ubuntu.com/10413705/](http://paste.ubuntu.com/10413705/)

'cat /etc/X11/Xorg.conf' after 'sudo nvidia-xconfig' looks like this:
[http://paste.ubuntu.com/10413654/](http://paste.ubuntu.com/10413654/)

'cat /etc/X11/Xorg.conf' after 'sudo nvidia-xconfig' looks like this:
[http://paste.ubuntu.com/10413630/](http://paste.ubuntu.com/10413630/)

'nvidia-settings -h | head -2'
nvidia-settings:  version 346.35  (buildmeister@swio-display-x86-rhel47-09)  Sat Jan 10 21:57:03 PST 2015

---

### Post by Bashing-om on 2015-02-25
chris137; Humm ....

A lot of old nvidia modules still on the system ... driver conflicts at some level, even though 'nvidia-settings' indicates the desired driver is installed ??
Before purging once more ALL Nvidia drivers, let's insure there is but one source for obtaining the driver:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

I bet -If I knew how for sure - there could be some tweaks done on the '/etc/X11/Xorg.conf'  file. Particularly in the "monitor" and "device" sections to give the system some additional help. But let's leave it for now 'till others can offer a comment.

[INDENT][INDENT]there can be only 1
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-02-25
cat -n /etc/apt/sources.list
[http://paste.ubuntu.com/10414296/](http://paste.ubuntu.com/10414296/)

tail -v -n +1 /etc/apt/sources.list.d/*
[http://paste.ubuntu.com/10414319/](http://paste.ubuntu.com/10414319/)

But I downloaded the driver directly from nvidia:
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)
Actually there was a new driver released yesterday. Maybe I just should try that one?

I used sudo apt-get purge nvidia* I think. Shouldn't that have removed the old drivers?
Honestly I don't even know where they come from since I've never had a nvidia-card before.

---

### Post by Bashing-om on 2015-02-25
chris137; Well;

While we are awaiting others greater knowledge,
Unrelated (?) but warrants attention:
> 
deb-src [http://ppa.launchpad.net/mixxx/mixxx/ubuntu](http://ppa.launchpad.net/mixxx/mixxx/ubuntu) precise main
deb-src [http://ppa.launchpad.net/skype-wrapper/ppa/ubuntu](http://ppa.launchpad.net/skype-wrapper/ppa/ubuntu) precise main

should be changed to 'trusty'. trusty is supported in both PPAs

Rather than downloading the driver from nvidia web site, consider installing from PPA, such that the driver is not broke in a kernel upgrade.
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
I often see as highly recommended and tested to work !

As you have installed those drivers from the Nvidia site, they are not under the auspice of the package management system. We will have to jump through some hoops to remove them I expect.
As we do not have the *.run files for them, could get dicey . Only one I see is for the 346 version.
I be considering what I think is the better way to proceed in the removal of the old drivers.

[INDENT][INDENT][INDENT]Sometimes I got to learn better
[/INDENT][/INDENT][/INDENT]

---

### Post by chris137 on 2015-02-25
Actually we do have the .run file since that is what I downloaded there.
*run --uninstall should do the trick as I read.
I've added the rep already.
Would I simply be installing the driver using apt-get install **nvidia-graphics-drivers-346**?

---

### Post by Bashing-om on 2015-02-25
chris137; Well;

Honestly, I do not think executing the --uninstall option from the 346 .run file will affect the older modules.
and yeah: To install from Mike's PPA
```

sudo add-apt-repository ppa:mamarley/nvidia
sudo apt-get update
sudo apt-get install nvidia-346

```
as the 346 driver is not available in our repository.

I would feel the better if this were done after all other modules for Nvidia graphics have been removed.

[INDENT][INDENT]many paths to an end
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-02-25
Oh, did not realize you meant the old ones.
I also have no clue how to do that.

Maybe someone different here can help?

---

### Post by Bashing-om on 2015-02-25
chris137; Hey;

> **chris137 said:**
> Oh, did not realize you meant the old ones.
I also have no clue how to do that.

Maybe someone different here can help?

Many eyes 'see' this thread there is a good chance we will get good guidance in this matter.

Given time we will figure this out. I would feel much better if we eliminate the possibility of conflicts and interference. A nice clean slate to work from; clear my mind to focus my attention on removing those old modules.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-02-25
Let's hope that.
In the meantime I feel like I did not really explain what I mean by "flickering".
The issue I have is that (I think only) in scrollable areas of windows a rectangular part starts flickering as if I'd be scrolling up and down very fast. Sometimes there are more of these areas overlapping which can cover the whole window.
I only watched this behaviour on thunderbird and firefox. I must say that these two are the applications I interact with the most.

Right now I can't really give a better description of it. If you got questions just ask.

---

### Post by Bashing-om on 2015-02-27
chris137: Hey, hey;

While we await others with greater experience to assist; let's re-focus our attention to 'cuda'. See if we can determine what it will take to remove this conflict with nvidia-prime.
As we have:
> 
ii libcuda1-331-updates 331.113-0ubuntu0.0.4 amd64 NVIDIA CUDA runtime library

What returns:
```

ls -al /opt
ls -al ~/NVIDIA_GPU_Computing_SDK 
sudo echo $PATH

```

To this time I have yet to come up with a means that I am comfortable with to remove those old Nvidia files and modules. I am still look'n and think'n .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-02-27
ls -al /opt only gives
drwxr-xr-x  6 root root  4096 Jan  3 23:51 .
drwxr-xr-x 25 root root 12288 Feb 27 16:21 ..
drwxr-xr-x  4 root root  4096 Feb  2 13:42 google
drwxr-xr-x  3 root root  4096 Aug 28  2014 spotify
drwxr-xr-x  6 root root  4096 Jan  3 23:51 teamviewer
drwxr-xr-x  4 root root  4096 Jan  3 23:41 teamviewer9

somehting called 'NVIDIA_GPU_Computing_SDK' is nowhere to be found in my system

sudo echo $PATH
/usr/games:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

---

### Post by Bashing-om on 2015-02-27
chris137; Curious, and curious;

I do not think there is anything left to work with, and I do expect it to be safe to manually remove that 'cuda' file.
But 1st; what results:
```

sudo apt-get purge --auto-remove nvidia-cuda-toolkit

```
when and IF that returns void:
Let's prepare to manually remove them.
```

sudo find / -name "libcuda*"
sudo find / -name cuda

```

I so hate stepping out the bounds of the package manager, but we can fix anything we break .

[INDENT][INDENT]safety is no accident
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-02-27
Actually it returns the following:
Some is German but I think you get the idea.
Should I proceed with it?
Package 'nvidia-cuda-toolkit' is not installed, so not removed
Die folgenden Pakete werden ENTFERNT:
  bbswitch-dkms* lib32gcc1* libcuda1-331-updates* libprotobuf-lite7*
  libqt4-webkit* libvamp-sdk2* linux-headers-3.13.0-40*
  linux-headers-3.13.0-40-generic* linux-headers-3.13.0-43*
  linux-headers-3.13.0-43-generic* linux-headers-3.13.0-44*
  linux-headers-3.13.0-44-generic* linux-image-3.13.0-40-generic*
  linux-image-3.13.0-43-generic* linux-image-3.13.0-44-generic*
  linux-image-extra-3.13.0-40-generic* linux-image-extra-3.13.0-43-generic*
  linux-image-extra-3.13.0-44-generic* python-cssselect* python-pyasn1*
  python-pycurl* python-queuelib* python-twisted* python-twisted-conch*
  python-twisted-lore* python-twisted-mail* python-twisted-names*
  python-twisted-news* python-twisted-runner* python-twisted-words*
  python-w3lib* screen-resolution-extra* xawtv-plugins*
0 aktualisiert, 0 neu installiert, 33 zu entfernen und 7 nicht aktualisiert.
Nach dieser Operation werden 846 MB Plattenplatz freigegeben.
Möchten Sie fortfahren? [J/n]

Thanks for helping me btw.
Would never get trough this without help.

---

### Post by efflandt on 2015-02-27
> **chris137 said:**
> Let's hope that.
In the meantime I feel like I did not really explain what I mean by "flickering".
The issue I have is that (I think only) in scrollable areas of windows a rectangular part starts flickering as if I'd be scrolling up and down very fast. Sometimes there are more of these areas overlapping which can cover the whole window.
I only watched this behaviour on thunderbird and firefox. I must say that these two are the applications I interact with the most.

Right now I can't really give a better description of it. If you got questions just ask.

The flickering can be fixed by doing something in **compizconfig-settings-manager**, but I do not know if that is installed by default.  See if it is with:```
dpkg-query -l compiz* | grep ii
```If not then:```
sudo apt-get update
sudo apt-get install compizconfig-settings-manager
```Then open **CompizConfig Settings Manager** from Dash (top icon in Unity bar), scroll down to Utility and in Workarounds check **Force full screen redraws (buffer swap) on repaint**. I don't know if you also need to check **Force complete redraw on initial damage**, or if that is checked by default (it is checked on mine).

I am currently using **nvidia-346** package from xorg-edgers ppa (which includes everything related) and have not had any problems:```
efflandt@XPS-8100-1404:~$ dpkg-query -l nvidia* | grep ii
ii  nvidia-346                                            346.47-0ubuntu1~xedgers14.04.1                         amd64        NVIDIA binary driver - version 346.47
ii  nvidia-opencl-icd-346                                 346.47-0ubuntu1~xedgers14.04.1                         amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                                  amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       346.47-0ubuntu1~xedgers14.04.1                         amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-settings-updates                               346.35-0ubuntu1~xedgers14.04.1                         amd64        Transitional package for nvidia-settings
```

---

### Post by chris137 on 2015-02-27
I tried that now.
It seems to be installed by default since I do not remember installing it manually (could be possible though).
I checked **Force full screen redraws (buffer swap) on repaint**, **Force complete redraw on initial damage** is checked by default.

Actually today I did not notice any flickering (might be used to it?).
Maybe it realized I tried to fix it and fled.

Removing those old drivers should be done anyway I guess.

---

### Post by Bashing-om on 2015-02-27
chris137; Ho Boy !


See efflandt's last ( Thanks Heaps !). Sure looks like worth a shot !

That sucker , libcuda* , is sure embedded deep !
I get :
```

sysop@1404mini:~$ sudo find / -name "libcuda*"
sysop@1404mini:~$

```
no return, as I do not have 'cuda' not 'Nvidia graphics' on my system.
A scary thought to start messing about with the linux-headers and python files ! We had best know what we are doing and getting into, before we take that step.
Let's do some poking and see what we can find out:
```

apt-cache rdepends bbswitch-dkms
apt-cache rdepends libprotobuf-lite7
apt-cache rdepends python-cssselect
apt-cache rdepends python-pycurl
apt-cache rdepends python-twisted-mail

``` as none of these are in a default install. We do want to know where they lead to.

For now, while I deliberate, get the system updated:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
'dist-upgrade' has nothing to do with a new release; It will install the latest kernel .

An aside; Code tags !
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
The use of "code tags" maintains the formatting and promotes readability ( as much code as we look at in a days time, sure helps !)

Started out "such a simple thing"
[INDENT][INDENT][INDENT]just goes to show
[INDENT][INDENT][INDENT]"never can tell"
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris137 on 2015-02-27
Oh, why don't you just kill me?
The card crashed again just now... Why the hell?
Pretty unlikely I got a card with the same fault again.
Must be the driver then, right? Never had problems even remote to this with my old one.
In fact I can't remember any at all.
Did your steps after I calmed down again.

```
** sudo find / -name "libcuda*"**
/usr/share/doc/libcuda1-331-updates
/usr/lib/i386-linux-gnu/libcuda.so
/usr/lib/i386-linux-gnu/libcuda.so.1
/usr/lib/i386-linux-gnu/libcuda.so.346.35
/usr/lib/x86_64-linux-gnu/libcuda.so
/usr/lib/x86_64-linux-gnu/libcuda.so.1
/usr/lib/x86_64-linux-gnu/libcuda.so.346.35
/var/lib/dpkg/info/libcuda1-331-updates.postrm
/var/lib/dpkg/info/libcuda1-331-updates.md5sums
/var/lib/dpkg/info/libcuda1-331-updates.list
/var/lib/dpkg/info/libcuda1-331-updates.postinst
/var/lib/dpkg/info/libcuda1-331-updates.shlibs
```
```
** apt-cache rdepends bbswitch-dkms**
bbswitch-dkms
Reverse Depends:
  bbswitch-dkms:i386
 |bumblebee
  nvidia-prime
```

```
** apt-cache rdepends libprotobuf-lite7**
libprotobuf-lite7
Reverse Depends:
```

```
** apt-cache rdepends python-cssselect**
python-cssselect
Reverse Depends:
  scrapy-0.24
  scrapy-0.25
  scrapy-0.24
  scrapy-0.23
  scrapy-0.22
  scrapy-0.21
  scrapy-0.20
  scrapy-0.19
  python-pyquery
  calibre
```

```
**apt-cache rdepends python-pycurl**
python-pycurl
Reverse Depends:
  jockey-common
  mythnetvision
  python-software-properties
  mythbuntu-bare-client
  python-bzrlib
  landscape-client
  python-pycurl:i386
  mythnetvision
  xapers
  webservice-office-zoho
  virtaal
  turtleart
  python-software-properties
  python-smartpm
  python-ganeti-rapi
  python-braintree
  photo-uploader
  penguintv
  nsscache
  mythbuntu-bare-client
  miro
  ganeti
  gajim
  fence-agents
  debpartial-mirror
  system-config-printer-gnome
  python-urlgrabber
  python-tornado
  python-pycurl-dbg
  python-cupshelpers
  python-bzrlib
  landscape-client
```

```
**apt-cache rdepends python-twisted-mail**
python-twisted-mail
Reverse Depends:
  sat-xmpp-core
  python-scrapy
  python-ldaptor
  ibid
  cardstories
  calendarserver
  buildbot
  python-twisted
```

Updates only found some language-packs. I think I keep it as uptodate as I can.

---

### Post by pissedoffdude on 2015-02-28
Are you using the latest driver? I have that same card on one of my boxes and I use the official nvidia drivers (from the .run) without any issues.  Ubuntu's and some I've gotten from external repos have always been problematic for me.  The easier approach (for me) to install it is (though you REALLY have to be mindful if you use this approach):

1) Use the restricted drivers manager to install whichever version of the nvidia drivers that your version of Ubuntu ships with so that it blacklists the nouveau driver (you don't need to do this if you manually blacklist it, but I find this way easier since it installs the tools required for compiling the driver as well)
2) Download the latest .run to the directory of your choosing
3) sudo service lightdm stop (or whichever display manager you're using, just kill your display manger)
4) sudo ./full/path/to/run/file or sh /fullpath/path/to/nvidia/run/file
5) Install the 32-bit libraries when prompted
6) sudo nvidia-xconfig
7) sudo reboot

Do note that this approach leads to having to re-install the driver from the .run every time there's a kernel update, so be sure to keep a copy of the .run file somewhere in case you can't load the GUI.

EDIT: for step 4: don't forget to chmod +x the run if you execute it with ./full/path/to/run

---

### Post by chris137 on 2015-02-28
I did exactly what you mentioned in 2-7
But I Do Not understand 1. Could you explain that?
I'll go to sleep now finally. 
Also my Phone tries to convince me to stop writing english.

---

### Post by pissedoffdude on 2015-02-28
I think you're good to go if you followed 2-7.  Does the issue persist?  By step 1, I meant pull up the software sources.  There are several tabs here.  One of them is for drivers and there you can install the NVIDIA drivers.  I recommended installing the drivers from that tab first because it would blacklist the nouveau drivers and install the tools required for building the drivers from the *.run file.  But if you've successfully installed the drivers from the *.run file without any issue, that's fine and you can disregard the 1st step. 

You should sporadically open the NVIDIA control panel just to monitor the temp if this doesn't resolve it

---

### Post by chris137 on 2015-02-28
These steps were pretty much the first thing I tried.
See here: [http://ubuntuforums.org/showthread.php?t=2265505&p=13232046#post13232046](http://ubuntuforums.org/showthread.php?t=2265505&p=13232046#post13232046)

That tab looks like this for me:
[IMG]http://pic.dnsts.de/u6REjR.png[/IMG]
First one says something like 'graphics driver nouveau of xserver-xorg-nouveau is used (Open source)
Second one should be clear.
Last one is 'Keep using a manually installed driver'
As you can see i can't choose anything else. Maybe because I'm not root?
I don't seem to be able to open it using sudo.
Any ideas?

---

### Post by Bashing-om on 2015-02-28
chris137;  - pissedoffdude; ......

The situation is that there is no driver available in the software repository for the 750ti; that leave only 2 recourses:
1) install from a PPA ( 3 that I am aware of)
2) install from the Nvidia site

Now take a look, I see a lot of conflicts, there is still 'cuda' and to compound the situation is 'BumbleBee'. I must assume at some point these were not properly removed and I do think a conflict in drivers is in effect. Both in the build process and the use of.

As to what we can do to resolve these conflicts and still maintain a stable system - that maintaining stability has me deeply concerned - I honestly do not know. It has now become a process of learning here for me also . The outputs do show how deeply intertwined everything is.

At this point the quickest easiest way forward is to back up your personal files, and do a clean fresh install .. However, doing so, we learn nothing much from this situation. Then install the 346 driver. I have seen where some have been able to get the 331 version to work. The 331 version is in the software repository. But Nvidia does recommend the 346 version .

As we no longer have an UN-install script for 'cuda' we have 2 courses ...
a) install cuda - maybe it will - and then try the uninstall file .
b) manually track down all the files and manually remove them, break the system possibly, and then fix the system .

I honestly again do not know what the better approach here is.

Then there is 'BumbleBee' to contend with ....

All this to get a reliable Nvidia 346 driver installed.
-----------------------------
If we are to proceed with a manual intervention I now want to see what that involves:
post back the output of :
```

cat /var/lib/dpkg/info/libcuda1-331-updates.list
cat /var/lib/dpkg/info/libcuda1-331-updates.postrm

```
so we compare what was installed as to what the uninstaller would remove for 'cuda'.

Next we need to look at 'BumbleBee"
```

sudo find / -name bumblebee

``` to get some direction on how to cope with 'bumblebee'.

Again for drivers ;
[INDENT][INDENT]there can be only one
[INDENT][INDENT][INDENT]else a conflict arises 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris137 on 2015-02-28
Forgot that in my post before:
Beside other things I already monitor the temp on my desktop. It was 38°C (100°F) at the time of the crash. That should be no critical temp at all.

```
-$ cat /var/lib/dpkg/info/libcuda1-331-updates.list
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libcuda1-331-updates
/usr/share/doc/libcuda1-331-updates/copyright
/usr/share/doc/libcuda1-331-updates/changelog.Debian.gz
/usr/lib
/usr/lib/i386-linux-gnu
/usr/lib/i386-linux-gnu/libcuda.so.331.113
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/libcuda.so.331.113
/usr/lib/i386-linux-gnu/libcuda.so.1
/usr/lib/i386-linux-gnu/libcuda.so
/usr/lib/x86_64-linux-gnu/libcuda.so.1
/usr/lib/x86_64-linux-gnu/libcuda.so
```
```
-$ cat /var/lib/dpkg/info/libcuda1-331-updates.postrm
#!/bin/sh
set -e
# Automatically added by dh_makeshlibs
if [ "$1" = "remove" ]; then
    ldconfig
fi
# End automatically added section
```
```
-$ sudo find / -name bumblebee | pastebinit
You are trying to send an empty document, exiting.
```
which probably means there is nothing.

Starting over completely crossed my mind too.
But I'd like to avoid that. I can guarantee there will be at least one different thing not working afterwards.

---

### Post by Bashing-om on 2015-02-28
chris137; Well, OK ;

We proceed on to manually intervening:
I must admit that I have been chasing my tail as per:
```

/usr/lib/i386-linux-gnu/libcuda.so.346.35
/usr/lib/x86_64-linux-gnu/libcuda.so.346.35

```
it do appear that 'cuda' is installed as a part of the Nvidia driver installation ! Whereas I had "assumed" 'cuda' to be a separate entity .(from prior experience getting 'cuda' to work in other situations) .

Think'n now all we have to do is remove the 331 version remnants of the Nvidia driver.
Rather than hold this thread open while I look, I post what I have  here and re-think what we must do to remove those remnants. As well what might result.

[INDENT][INDENT]3 steps forward and
[INDENT][INDENT]4 back
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-02-28
chris137; Still,

Struggling not to resort to a manual intervention. 
What returns:
```

cat /sys/module/nvidia/version
ls -ld /lib/nvidia*
sudo apt-cache search nvidia-sett*

``` maybe find something the package manager can get a handle on to take care of the 331 remnants.
The last thing I want to do is risk breaking the system to the point we can not (RE-)install what is required.

[INDENT][INDENT]safety is no accident
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-02-28
```
-$ cat /sys/module/nvidia/version
346.35
```
/lib/nvidia* does not exist

```
-$ sudo apt-cache search nvidia-sett*
nvidia-settings - Werkzeug zum Einrichten des NVIDIA-Grafiktreibers
nvidia-settings-304 - Transitional package for nvidia-settings
nvidia-settings-304-updates - Transitional package for nvidia-settings
nvidia-settings-310 - Transitional package for nvidia-settings
nvidia-settings-310-updates - Transitional package for nvidia-settings
nvidia-settings-313-updates - Transitional package for nvidia-settings
nvidia-settings-319 - Transitional package for nvidia-settings
nvidia-settings-319-updates - Transitional package for nvidia-settings
nvidia-settings-experimental-304 - Transitional package for nvidia-settings
nvidia-settings-updates - Transitional package for nvidia-settings
sensors-applet - Display readings from hardware sensors in your Gnome panel
```
This sure looks like there is too much.

---

### Post by Bashing-om on 2015-02-28
chris137; Welp !

OK, let's start this, and see where we go:
```

sudo apt-get autoremove nvidia-304*
sudo apt-get --purge remove nvidia-304*
sudo apt-get autoremove nvidia-310*
sudo apt-get --purge remove nvidia-310*
sudo apt-get autoremove nvidia-313*
sudo apt-get --purge remove nvidia-313*
sudo apt-get autoremove nvidia-319*
sudo apt-get --purge remove nvidia-319*
sudo apt-get autoremove nvidia-331*
sudo apt-get --purge remove nvidia-331*
sudo apt-get autoremove
sudo apt-get autoclean

```
does the package manager take care of removing the "libcuda.so.331.113" files ?
Look:
```

ls -al /usr/lib/i386-linux-gnu/

``` see what we have no to do manually (uuhhggg) .

[INDENT][INDENT][INDENT]and away we go 
[INDENT][INDENT][INDENT]up up and away ?
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris137 on 2015-02-28
I just went into /usr/lib/i386-linux-gnu/ and looked myself.
These are the only libcuda files there which seems to be alright:
```
lrwxrwxrwx   1 root root       12 Feb 25 19:06 libcuda.so -> libcuda.so.1
lrwxrwxrwx   1 root root       17 Feb 25 19:06 libcuda.so.1 -> libcuda.so.346.35
-rwxr-xr-x   1 root root 13121068 Feb 25 19:06 libcuda.so.346.35
```
sudo apt-get autoremove nvidia-304* wants to remove all these packages which you were sceptical about before if I understood that correctly.
But I guess if linux wants to get rid of those it's no problem right?
```
  bbswitch-dkms lib32gcc1 libcuda1-331-updates libprotobuf-lite7 libqt4-webkit
  libvamp-sdk2 linux-headers-3.13.0-40 linux-headers-3.13.0-40-generic
  linux-headers-3.13.0-43 linux-headers-3.13.0-43-generic
  linux-headers-3.13.0-44 linux-headers-3.13.0-44-generic
  linux-image-3.13.0-40-generic linux-image-3.13.0-43-generic
  linux-image-3.13.0-44-generic linux-image-extra-3.13.0-40-generic
  linux-image-extra-3.13.0-43-generic linux-image-extra-3.13.0-44-generic
  python-cssselect python-pyasn1 python-pycurl python-queuelib python-twisted
  python-twisted-conch python-twisted-lore python-twisted-mail
  python-twisted-names python-twisted-news python-twisted-runner
  python-twisted-words python-w3lib screen-resolution-extra xawtv-plugins
```
This would free 846MB. What?
Just holding back a second because you had concerns about these earlier.

---

### Post by Bashing-om on 2015-02-28
chris137; Well ..

Not quite as skeptical as I was after doing all this research .... but, before proceeding let's check the kernel you are booting.
```

uname -r

```
If that comes back as " 3.13.0-46-generic" or " 3.13.0-45-generic " ; I think it safe to proceed.
We got to take a plunge somewhere and see where to go .
The files 'last accessed' Feb 25 tends to make me believe they are all for the 346 version of the driver ... what a relieve !
so yeah go ahead:
sudo apt-get autoremove and --purge away !
afterward let's run :
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg -C

```
just to make sure the package manager is in a happy state.

[INDENT][INDENT]bated breath
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-02-28
3.13.0-46-generic it is.
Only time something happened was with 
```
-$ sudo apt-get autoremove nvidia-304*
```

```
-$ sudo dpkg -C
Für die folgenden Pakete fehlt die MD5-Prüfsummen-Datei in der Datenbank,
sie müssen erneut installiert werden:
 libjson0:amd64       JSON manipulation library (transitional package)
 libjson0:i386        JSON manipulation library (transitional package)
```
Meaning something like
For the following packets the MD5-checksum is missing in the database, they have to be installed again.
Looks like it's related to what we just did right?

---

### Post by Bashing-om on 2015-02-28
chris137' Moving along smartly ;


This I do not think is a big deal:
> 
libjson0:
Looks like it's related to what we just did right?

Maybe, but I doubt it. fix:
```

sudo apt-get install --reinstall libjson0:amd64
sudo apt-get install --reinstall libjson0:i386

``` as the package manager advises.
What have we got now ? any change ?
```

sudo find / -name nvidia
sudo find / -name "libcuda*"

```

Maybe with a great amount of hope, all cleaned up.

[INDENT][INDENT]hey, it could happen
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-02-28
Yup, everything fixed over there.
I'm not sure we used that command before..
```
-$ sudo find / -name nvidia
/lib/modules/3.13.0-36-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.13.0-36-generic/kernel/drivers/video/nvidia
/lib/modules/3.13.0-35-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.13.0-35-generic/kernel/drivers/video/nvidia
/lib/modules/3.13.0-39-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.13.0-39-generic/kernel/drivers/video/nvidia
/lib/modules/3.8.0-44-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.8.0-44-generic/kernel/drivers/video/nvidia
/lib/modules/3.13.0-45-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.13.0-45-generic/kernel/drivers/video/nvidia
/lib/modules/3.13.0-37-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.13.0-37-generic/kernel/drivers/video/nvidia
/lib/modules/3.13.0-46-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.13.0-46-generic/kernel/drivers/video/nvidia
/usr/share/nvidia
/usr/lib/nvidia
/usr/src/linux-headers-3.13.0-34/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.13.0-34/drivers/video/nvidia
/usr/src/linux-headers-3.13.0-36/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.13.0-36/drivers/video/nvidia
/usr/src/linux-headers-3.13.0-35-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.13.0-39/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.13.0-39/drivers/video/nvidia
/usr/src/linux-headers-3.13.0-45-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.13.0-46/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.13.0-46/drivers/video/nvidia
/usr/src/linux-headers-3.13.0-34-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.13.0-39-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.13.0-37-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.13.0-45/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.13.0-45/drivers/video/nvidia
/usr/src/linux-headers-3.13.0-35/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.13.0-35/drivers/video/nvidia
/usr/src/linux-headers-3.13.0-36-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.13.0-37/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.13.0-37/drivers/video/nvidia
/usr/src/linux-headers-3.13.0-46-generic/include/config/fb/nvidia
/etc/apparmor.d/abstractions/nvidia
/var/lib/nvidia
/var/lib/dkms/nvidia
/sys/bus/pci/drivers/nvidia
/sys/module/drm/holders/nvidia
/sys/module/nvidia
/proc/irq/47/nvidia
/proc/driver/nvidia
```
```
-$ sudo find / -name "libcuda*"
/usr/lib/i386-linux-gnu/libcuda.so.1
/usr/lib/i386-linux-gnu/libcuda.so.346.35
/usr/lib/x86_64-linux-gnu/libcuda.so.1
/usr/lib/x86_64-linux-gnu/libcuda.so.346.35
/var/lib/dpkg/info/libcuda1-331-updates.postrm
/var/lib/dpkg/info/libcuda1-331-updates.list
```
Well.. 331 still there :/

---

### Post by Bashing-om on 2015-02-28
chris137; Hey !

Looking much better, Cleaned up a bunch.
This:
> 
/var/lib/dpkg/info/libcuda1-331-updates.postrm
/var/lib/dpkg/info/libcuda1-331-updates.list

are just scripts for the installer as a control and as such has no real bearing on anything executable. 'cat' them and see for yourself, they are just ASCII text files.When we are all done we will remove them manually !

Why we still have ALL these:
> 
/lib/modules/3.13.0-35-generic/kernel/drivers/video/nvidia

old modules around is a mystery to me .
Maybe best to look about doing a bit of housecleaning before we tackle them:
What returns:
```

ls -al /boot
dpkg -l | grep linux-
dpkg -l | grep -i nvidia

```
housecleaning I expect might do us a world of good right now.
//

But for a fact, 
[INDENT][INDENT]gets any brighter, 
[INDENT][INDENT][INDENT]we gonna put on sun-glasses
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-01
Had to get some sleep already :D

```
**-$ ls -al /boot**
-rw-r--r--  1 root root  1162712 Aug 13  2014 abi-3.13.0-34-generic
-rw-r--r--  1 root root  1163858 Aug 15  2014 abi-3.13.0-35-generic
-rw-r--r--  1 root root  1163858 Sep  4 00:24 abi-3.13.0-36-generic
-rw-r--r--  1 root root  1164489 Sep 23 00:24 abi-3.13.0-37-generic
-rw-r--r--  1 root root  1164547 Okt 28 15:25 abi-3.13.0-39-generic
-rw-r--r--  1 root root  1164967 Jan 13 21:12 abi-3.13.0-45-generic
-rw-r--r--  1 root root  1164852 Feb 26 20:46 abi-3.13.0-46-generic
-rw-r--r--  1 root root   921155 Jul 15  2014 abi-3.8.0-44-generic
-rw-r--r--  1 root root   165611 Aug 13  2014 config-3.13.0-34-generic
-rw-r--r--  1 root root   165652 Aug 15  2014 config-3.13.0-35-generic
-rw-r--r--  1 root root   165671 Sep  4 00:24 config-3.13.0-36-generic
-rw-r--r--  1 root root   165712 Sep 23 00:24 config-3.13.0-37-generic
-rw-r--r--  1 root root   165712 Okt 28 15:25 config-3.13.0-39-generic
-rw-r--r--  1 root root   165748 Jan 13 21:12 config-3.13.0-45-generic
-rw-r--r--  1 root root   165748 Feb 26 20:46 config-3.13.0-46-generic
-rw-r--r--  1 root root   154959 Jul 15  2014 config-3.8.0-44-generic
drwxr-xr-x  3 root root     4096 Mär  1 00:06 extlinux
drwxr-xr-x  6 root root    12288 Mär  1 00:06 grub
-rw-r--r--  1 root root 19163364 Sep 11 20:05 initrd.img-3.13.0-35-generic
-rw-r--r--  1 root root 19179809 Okt  3 15:31 initrd.img-3.13.0-36-generic
-rw-r--r--  1 root root 19180019 Okt  9 16:34 initrd.img-3.13.0-37-generic
-rw-r--r--  1 root root 19180469 Nov 15 02:17 initrd.img-3.13.0-39-generic
-rw-r--r--  1 root root 27592868 Feb 21 00:29 initrd.img-3.13.0-45-generic
-rw-r--r--  1 root root 27595944 Feb 27 15:57 initrd.img-3.13.0-46-generic
-rw-r--r--  1 root root 16538373 Aug  8  2014 initrd.img-3.8.0-44-generic
-rw-r--r--  1 root root   176500 Mär 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mär 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mär 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3381262 Aug 13  2014 System.map-3.13.0-34-generic
-rw-------  1 root root  3386444 Aug 15  2014 System.map-3.13.0-35-generic
-rw-------  1 root root  3386479 Sep  4 00:24 System.map-3.13.0-36-generic
-rw-------  1 root root  3386945 Sep 23 00:24 System.map-3.13.0-37-generic
-rw-------  1 root root  3386936 Okt 28 15:25 System.map-3.13.0-39-generic
-rw-------  1 root root  3389258 Jan 13 21:12 System.map-3.13.0-45-generic
-rw-------  1 root root  3389458 Feb 26 20:46 System.map-3.13.0-46-generic
-rw-------  1 root root  3196521 Jul 15  2014 System.map-3.8.0-44-generic
-rw-------  1 root root  5797728 Aug 13  2014 vmlinuz-3.13.0-34-generic
-rw-------  1 root root  5806368 Aug 15  2014 vmlinuz-3.13.0-35-generic
-rw-------  1 root root  5806848 Sep  4 00:24 vmlinuz-3.13.0-36-generic
-rw-------  1 root root  5808832 Sep 23 00:24 vmlinuz-3.13.0-37-generic
-rw-------  1 root root  5808544 Okt 28 15:25 vmlinuz-3.13.0-39-generic
-rw-------  1 root root  5814112 Jan 13 21:12 vmlinuz-3.13.0-45-generic
-rw-------  1 root root  5814528 Feb 26 20:46 vmlinuz-3.13.0-46-generic
-rw-------  1 root root  5461488 Jul 15  2014 vmlinuz-3.8.0-44-generic
```
```
**-$ dpkg -l | grep linux-**
ii  linux-firmware                                              1.127.11                                            all          Firmware for Linux kernel drivers
ii  linux-generic                                               3.13.0.46.53                                        amd64        Complete Generic Linux kernel and headers
ii  linux-generic-lts-raring                                    3.13.0.46.53                                        amd64        Generic Linux kernel image and headers
ii  linux-generic-lts-trusty                                    3.13.0.46.53                                        amd64        Generic Linux kernel image and headers
ii  linux-headers-3.13.0-34                                     3.13.0-34.60                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic                             3.13.0-34.60                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-35                                     3.13.0-35.62                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                             3.13.0-35.62                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-36                                     3.13.0-36.63                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-36-generic                             3.13.0-36.63                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-37                                     3.13.0-37.64                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                             3.13.0-37.64                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-39                                     3.13.0-39.66                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic                             3.13.0-39.66                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-45                                     3.13.0-45.74                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                             3.13.0-45.74                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-46                                     3.13.0-46.76                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                             3.13.0-46.76                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       3.13.0.46.53                                        amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-raring                            3.13.0.46.53                                        amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-trusty                            3.13.0.46.53                                        amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-34-generic                               3.13.0-34.60                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                               3.13.0-35.62                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic                               3.13.0-36.63                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic                               3.13.0-37.64                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic                               3.13.0-39.66                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-40-generic                               3.13.0-40.69                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-43-generic                               3.13.0-43.72                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-44-generic                               3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-45-generic                               3.13.0-45.74                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-generic                               3.13.0-46.76                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-29-generic                                3.8.0-29.42~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-34-generic                                3.8.0-34.49~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-35-generic                                3.8.0-35.52~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-36-generic                                3.8.0-36.52~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-37-generic                                3.8.0-37.53~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-38-generic                                3.8.0-38.56~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-39-generic                                3.8.0-39.58~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-41-generic                                3.8.0-41.60~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-42-generic                                3.8.0-42.63~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-44-generic                                3.8.0-44.66~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-34-generic                         3.13.0-34.60                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                         3.13.0-35.62                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic                         3.13.0-36.63                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                         3.13.0-37.64                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                         3.13.0-39.66                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-40-generic                         3.13.0-40.69                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-43-generic                         3.13.0-43.72                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                         3.13.0-45.74                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                         3.13.0-46.76                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                         3.13.0.46.53                                        amd64        Generic Linux kernel image
ii  linux-image-generic-lts-raring                              3.13.0.46.53                                        amd64        Generic Linux kernel image
ii  linux-image-generic-lts-trusty                              3.13.0.46.53                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        3.13.0-46.76                                        amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-themes-debian                                      12-3                                                all          collection of boot loaders (theme metapackage)
ii  syslinux-themes-debian-wheezy                               12-3                                                all          collection of boot loaders (debian-wheezy theme)
```
```
**-$ dpkg -l | grep -i nvidia**
rc  libcuda1-331-updates                                        331.113-0ubuntu0.0.4                                amd64        NVIDIA CUDA runtime library
```

---

### Post by Bashing-om on 2015-03-01
chris137; Well ;

I am beginning to get an idea of what is going on here .
> 
ii  linux-headers-generic-lts-raring                            3.13.0.46.53                                        amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-trusty                            3.13.0.46.53<snip>

Do we have a conflict of interest here ? As 'raring' no longer exist . Hummm, clean up for sure for sure.
Once more, so I know what we have to contend with; post back:
```

lsb_release -a
cat /etc/issue
hwe-support-status --verbose

```
and then we clean house.

Sorta kinda expected something like this, but had not thought about Hard Ware Enablement stack. That do explain the why 'autoremove' did not perform as I anticipated.

[INDENT][INDENT]meanwhile, back at the ranch
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-01
```
-$ lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty
```
```
-$ cat /etc/issue
Ubuntu 14.04.2 LTS \n \l
```
hwe-support-status does not exist

---

### Post by Bashing-om on 2015-03-01
chris137; Well ;

Looks promising, let's start the housecleaning ! Small steps 'cause that is all my little mind can cope with.
```

sudo apt-get --purge remove linux-image-3.8.0-44-generic

```
kind of dis-concerting that there is no corresponding header file but let's see what happens>
IF that goes well, next is to tackle "linux-image-generic-lts-trusty" ;
next remove all the other "3.13.0-XX" kernels ;
next is deal with all those 'rc' marked kernels ;
And finally .. back to " libcuda1-331-updates" and clean that up.

seems like a lot but
[INDENT][INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-01
So if I understood that right this is what I'll do:
```
-$ sudo apt-get --purge remove linux-image-3.8.0-44-generic
-$ sudo apt-get --purge remove linux-image-generic-lts-trusty
# all 3.13.0-XX kernels
-$ sudo apt-get --purge remove linux-image-3.13.0-*
#also those -extra things? if so:
-$ sudo apt-get --purge remove linux-image-extra-3.13.0*
#all rc-marked kernels
-$ sudo apt-get --purge remove linux-image-3.8.0-29-generic
-$ sudo apt-get --purge remove linux-image-3.8.0-3*
-$ sudo apt-get --purge remove linux-image-3.8.0-41-generic
-$ sudo apt-get --purge remove linux-image-3.8.0-42-generic
#only if not already covered above
-$ sudo apt-get --purge remove linux-image-extra-3.13.0-34-generic
-$ sudo apt-get --purge remove linux-image-extra-3.13.0-40-generic
-$ sudo apt-get --purge remove linux-image-extra-3.13.0-43-generic
-$ sudo apt-get --purge remove linux-image-extra-3.13.0-44-generic
#finally libcuda
-$ sudo apt-get --purge remove libcuda1-331-updates
```
First one took some time but is finishsed while I put together the above. There seem to be no errors.

If everything is correct I'll proceed to do that.

---

### Post by Bashing-om on 2015-03-01
chris137 !

NO!!!
> 
sudo apt-get --purge remove linux-image-extra-3.13.0*


That wildcard '*' will also take out the kernels we want to keep !

gimme a bit and I formulate the next step.

[INDENT][INDENT]small steps, small steps .. contain the damage
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-03-01
chris137 ; Sheeesshhh ;

Now my little mind is confused/
You did:
> 
sudo apt-get --purge remove linux-image-3.8.0-44-generic

Is
"First one took some time " only in reference to the 3.8.o-44-generic kernel. Nothing else has been removed ( I hope I hope !)...
I am so sorry if I mislead you - small steps !

[INDENT][INDENT]it's buntu
[INDENT][INDENT]always fixable
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-01
Yes, until now I only did
```
sudo apt-get --purge remove linux-image-3.8.0-44-generic
```
You said "next remove all the other "3.13.0-XX" kernels" which looks to me like a wildcard like 3.13.0-* should be exactly what does that.

---

### Post by Bashing-om on 2015-03-01
chris137; Wheww

easy breath. Sorry that my attempt at brevity (-XX) caused a misconception.

OK, onto the next step. I had considered to 'look' first before leaping, but that 'raring' kernel needs gone no matter the result so no beating around the bush, here we go: next do:
```

sudo apt-get --purge remove linux-image-generic-lts-raring
sudo apt-get --purge remove linux-generic-lts-raring
sudo apt-get --purge remove linux-headers-generic-lts-raring

```
See if that flies and if there is any damage we need to cope with at this point.

[INDENT][INDENT]proceeding merrily on our way
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-01
Alright, all done.
No errors appeared. Went very fast, too.
Step to step is always a good idea - especially when I only understand half of what I'm doing here :P

---

### Post by Bashing-om on 2015-03-01
chris137; Great ..

Moving on along ..
//and hey, I never want to move so fast that we can not take the time to explain what/why we are doing where, this forum also functions as a foundation of teaching and knowledge - ask ! //

So far so good .. now the current release kernels ;
Rather than a complex single command, let's do this also simple and easy - understandable:
```

sudo apt-get purge linux-image-3.13.0-{34,35,36,37,39,40,43,44}-generic
sudo apt-get purge linux-image-extra-3.13.0-40-generic
sudo apt-get purge linux-headers-3.13.0-{34,35,36,37,39}-generic
sudo apt-get purge linux-headers-3.13.0-{34,35,36,37,39}

```
as you can see things are a bit convoluted as images and headers do not match ..I can not imagine how this state of affairs came about . I think though when all done all will be in good shape. 

When all that completes -one command at a time. let's get a fresh look:
```

dpkg -l | grep linux-

```

see If I have missed anything.

[INDENT][INDENT]so close we can smell the finish
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-01
Now I know why sudo apt-get --purge remove linux-image-extra-3.13.0* would not have been very clever :lol:
While looking through the output of 'sudo apt-get purge linux-image-3.13.0-{34,35,36,37,39,40,43,44}-generic' I found this. Hope it's not completely out of context.
```
Löschen der Konfigurationsdateien von linux-image-3.13.0-37-generic (3.13.0-37.64) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.13.0-46-generic...
P: Writing config for /boot/vmlinuz-3.13.0-45-generic...
P: Writing config for /boot/vmlinuz-3.13.0-39-generic...
P: Writing config for Windows 7 (loader) on /dev/sda3...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
Entfernen von linux-image-extra-3.13.0-39-generic (3.13.0-39.66) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
Error! Module version 4.3.10_Ubuntu for vboxdrv.ko
is not newer than what is already found in kernel 3.13.0-39-generic (4.3.18).
You may override by specifying --force.
Error! Module version 4.3.10_Ubuntu for vboxnetadp.ko
is not newer than what is already found in kernel 3.13.0-39-generic (4.3.18).
You may override by specifying --force.

Good news! Module version 4.3.10_Ubuntu for vboxnetflt.ko
exactly matches what is already found in kernel 3.13.0-39-generic.
DKMS will not replace this module.
You may override by specifying --force.
Error! Module version 4.3.10_Ubuntu for vboxpci.ko
is not newer than what is already found in kernel 3.13.0-39-generic (4.3.18).
You may override by specifying --force.
rmdir: konnte »“ nicht entfernen: Datei oder Verzeichnis nicht gefunden
rmdir: konnte »“ nicht entfernen: Datei oder Verzeichnis nicht gefunden
rmdir: konnte »“ nicht entfernen: Datei oder Verzeichnis nicht gefunden
rmdir: konnte »“ nicht entfernen: Datei oder Verzeichnis nicht gefunden
Error! Problems with depmod detected.  Automatically uninstalling this module.
All done here.
```
Proceeded anyway. Hope that's no mistake.. Altough I got an error there too:
```
-$ sudo apt-get purge linux-headers-3.13.0-{34,35,36,37,39}-generic
...
dpkg: Warnung: Während Entfernens von linux-headers-3.13.0-39-generic ist Verzeichnis »/lib/modules/3.13.0-39-generic« nicht leer, wird daher nicht gelöscht
```
Meaning something like "While removing linux-headers-3.13.0-39-generic directory »/lib/modules/3.13.0-39-generic« is not empty and is therefore not removed.
Solution = Simply remove it manually?

Everything else went without any problems.

```
-$ dpkg -l | grep linux-
ii  linux-firmware                                              1.127.11                                            all          Firmware for Linux kernel drivers
ii  linux-generic                                               3.13.0.46.53                                        amd64        Complete Generic Linux kernel and headers
ii  linux-generic-lts-trusty                                    3.13.0.46.53                                        amd64        Generic Linux kernel image and headers
ii  linux-headers-3.13.0-45                                     3.13.0-45.74                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                             3.13.0-45.74                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-46                                     3.13.0-46.76                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                             3.13.0-46.76                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       3.13.0.46.53                                        amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-trusty                            3.13.0.46.53                                        amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-45-generic                               3.13.0-45.74                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-generic                               3.13.0-46.76                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-29-generic                                3.8.0-29.42~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-34-generic                                3.8.0-34.49~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-35-generic                                3.8.0-35.52~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-36-generic                                3.8.0-36.52~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-37-generic                                3.8.0-37.53~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-38-generic                                3.8.0-38.56~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-39-generic                                3.8.0-39.58~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-41-generic                                3.8.0-41.60~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-42-generic                                3.8.0-42.63~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-34-generic                         3.13.0-34.60                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-43-generic                         3.13.0-43.72                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                         3.13.0-45.74                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                         3.13.0-46.76                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                         3.13.0.46.53                                        amd64        Generic Linux kernel image
ii  linux-image-generic-lts-trusty                              3.13.0.46.53                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        3.13.0-46.76                                        amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-themes-debian                                      12-3                                                all          collection of boot loaders (theme metapackage)
ii  syslinux-themes-debian-wheezy                               12-3                                                all          collection of boot loaders (debian-wheezy theme)

```

---

### Post by Bashing-om on 2015-03-01
chris137; Yuk;

Not at all prepared for this event:
> 
Checking for EXTLINUX directory... found.
&&
Error! Module version 4.3.10_Ubuntu for vboxdrv.ko
&&
is not newer than what is already found in kernel 3.13.0-39-generic (4.3.18).

I had seen that directory earlier, and I had wondered about it. do you have some type of Virtual Machine installed ?
Upfront. I know nothing about vbox ! Flying again by the seat of our pants.
Presently I do not know what we are going to do about :
> 
is not newer than what is already found in kernel 3.13.0-39-generic (4.3.18).
 -> time and effort will tell !

For now:
> 
Meaning something like "While removing linux-headers-3.13.0-39-generic directory »/lib/modules/3.13.0-39-generic« is not empty and is therefore not removed.
Solution = Simply remove it manually?

Most likely we will remove it manually;
Let's look 1st prior to jumping:
```

ls -al /usr/src
ls -al /lib/modules/

```

[INDENT][INDENT]cleanup time now ?
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-01
I do run Windows on vbox but I don't use it for anything essential. No harm if it stopped working.
```
~$ ls -al /usr/src
drwxr-xr-x 24 root root 4096 Feb  2 04:43 linux-headers-3.13.0-45
drwxr-xr-x  7 root root 4096 Feb  2 04:43 linux-headers-3.13.0-45-generic
drwxr-xr-x 24 root root 4096 Feb 27 15:56 linux-headers-3.13.0-46
drwxr-xr-x  7 root root 4096 Feb 27 15:56 linux-headers-3.13.0-46-generic
drwxr-xr-x  3 root root 4096 Feb 25 19:06 nvidia-346.35
drwxr-xr-x 12 root root 4096 Feb  3 12:21 virtualbox-4.3.10
```

```
~$ ls -al /lib/modules/
drwxr-xr-x  3 root root 4096 Mär  1 21:34 3.13.0-39-generic
drwxr-xr-x  6 root root 4096 Mär  1 00:05 3.13.0-45-generic
drwxr-xr-x  6 root root 4096 Mär  1 00:05 3.13.0-46-generic
```

---

### Post by Bashing-om on 2015-03-01
chris137; OK;

Looks fairly descent ; notwithstanding :
> 
drwxr-xr-x 12 root root 4096 Feb  3 12:21 virtualbox-4.3.10

anyway we can update vbox so it no longer depends on that old old 3.13.0-39-generic  kernel - that we NO NOT want on the system ???
Take care of vbox and I think the next is to take care of those packages marked 'rc' .


[INDENT][INDENT]what I do not know fills a bigger book
[INDENT][INDENT][INDENT]than what I do know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-01
Updated vbox from 4.3.10 to 4.3.22
While doing that these showed up
```
-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.3.10
Kernel:  3.13.0-39-generic (x86_64)
-------------------------------------


-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.3.10
Kernel:  3.13.0-45-generic (x86_64)
-------------------------------------


-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.3.10
Kernel:  3.13.0-46-generic (x86_64)
-------------------------------------
```
Looked primising at first but I don't actually see any change in the output. Just got more instead of less
```
~$ ls -al /usr/src
drwxr-xr-x 24 root root 4096 Feb  2 04:43 linux-headers-3.13.0-45
drwxr-xr-x  7 root root 4096 Feb  2 04:43 linux-headers-3.13.0-45-generic
drwxr-xr-x 24 root root 4096 Feb 27 15:56 linux-headers-3.13.0-46
drwxr-xr-x  7 root root 4096 Feb 27 15:56 linux-headers-3.13.0-46-generic
drwxr-xr-x  3 root root 4096 Feb 25 19:06 nvidia-346.35
lrwxrwxrwx  1 root root   32 Feb 12 17:35 vboxhost-4.3.22 -> ../share/virtualbox/src/vboxhost
```
```
~$ ls -al /lib/modules/
drwxr-xr-x  3 root root 4096 Mär  1 22:30 3.13.0-39-generic
drwxr-xr-x  5 root root 4096 Mär  1 22:30 3.13.0-45-generic
drwxr-xr-x  6 root root 4096 Mär  1 22:31 3.13.0-46-generic
drwxr-xr-x  3 root root 4096 Mär  1 22:30 3.8.0-31-generic
```

---

### Post by Bashing-om on 2015-03-01
chris137; Hey !

Looks good to me ... a proper symlink to the desired target.

OK, does vbox boot and any problems there >

[INDENT][INDENT]all systems go for cleanup ?
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-01
vbox is running just fine.
Did a reboot just now and linux is still alive too.

Everything ready I guess!

---

### Post by Bashing-om on 2015-03-01
chris137; Outstanding:

The state is 'rc', the package is removed, but the config files are not removed.
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package with the following command.
Now let’s remove all the packages marked as 'rc'.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

And now we finish the cleanup, and make sure the package manager is still in a happy happy state:
```

sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean
#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,A dist-upgrade will install new
#dependencies for packages already installed and may remove packages if they are no longer needed. This will not bring you to a new release of ubuntu. 
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg -C
sudo dpkg --configure -a

```


Oh Shucks not yet ...  ready .. to look at graphics ,, there is still 'libcuda1-331-updates ' to finish up with.
Get the above done and we pick up with this last little detail .
OK, then when all the above runs clean and 'libcuda' is dealt with , then , we are at the point of where we were a week ago to take a proper look at the graphics driver issue.
a) do we stay with where we are - all good now ?
b) do we (re-)install the OEM driver ( not the best option in my opinion);
c) do we install the proprietary driver from:
    [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia) ;
d) do we install the proprietary driver from:
     xorg-edgers ppa .

Your time, your effort, and your cleaned up system
[INDENT][INDENT]your call as to what ya want to do
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-01
Only one error I could spot:
```
dpkg: Warnung: Während Entfernens von unity-common ist Verzeichnis »/etc/compizconfig/upgrades« nicht leer, wird daher nicht gelöscht
```
not empty, not removed.

Everything worked fine.
This (over the few pages) also cleaned up almost 2GB of disk-space! My already pretty slim linux-partition gets smaller and smaller :D

So what about libcuda1-331-updates now?
A simple purge there or was that the issue all along?

About that driver..
I'd like to test the situation first for a few days.
There is no flickering anymore and the crash occured every few days so I will wait for one until we get into those drivers again.

---

### Post by Bashing-om on 2015-03-01
chris137; Humm ..

Sorry state, I am not bi-lingual - have a hard time even with English .. my poor upbring'n I guess.
As it is but a "warning" from "unity-common" it might be alright to ignore. But as we are looking into a graphics situation, and 'unity' is the display .. May as well see what we can do to resolve that warning too.

For now back to "libcuda" :
Tedious but worth the while and effort:
```

cat /var/lib/dpkg/info/libcuda1-331-updates.list

```
to get an updated listing of files.
OK, check and make sure None of the listed files exist :
for each file listed:
```

ls -al /usr/lib/i386-linux-gnu

```
as one instance.
If that file were to exist, one removes it thus:
```

sudo rm /usr/lib/i386-linux-gnu

```
None of them are needed anymore. I can foresee that all the files in "/usr/share/doc" are still present.
Removing these files will free up additional disk space and preclude any conflicts !

When all done looking and possibly removing listed files: we can now dispense with these control files.
```

sudo rm /var/lib/dpkg/info/libcuda1-331-updates.list
sudo rm /var/lib/dpkg/info/libcuda1-331-updates.postrm

```

And YES. let's let what we have done simmer and a few days with heavy usage and see what results.
Be aware that with the OEM driver, there is a good chance of breakage when the kernel is updated. That driver is built with the files and libraries present when installed, new kernels, libs and files can and do break that build.

[INDENT][INDENT]you do have sun-glasses on don't you ?
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-01
Sorry, meant to write something like 'as above'.#
It just says that the directoy was not empty and not removed, just like with 'sudo apt-get purge linux-headers-3.13.0-{34,35,36,37,39}-generic' back here: [http://ubuntuforums.org/showthread.php?t=2265505&page=7&p=13237450#post13237450](http://ubuntuforums.org/showthread.php?t=2265505&page=7&p=13237450#post13237450)

/var/lib/dpkg/info/libcuda1-331-updates.list does not exist

Anyway I'm not sure what you want to say with what comes next.
I know I should do something with those files listed in the - obviously non existent - file above, right?

---

### Post by Bashing-om on 2015-03-01
chris137; Humm ..

I guess the 'libcuda' control file got removed in that cleanup process... 
so we have the fall back:
```

-$ cat /var/lib/dpkg/info/libcuda1-331-updates.list
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libcuda1-331-updates
/usr/share/doc/libcuda1-331-updates/copyright
/usr/share/doc/libcuda1-331-updates/changelog.Debian.gz
/usr/lib
/usr/lib/i386-linux-gnu
/usr/lib/i386-linux-gnu/libcuda.so.331.113
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/libcuda.so.331.113
/usr/lib/i386-linux-gnu/libcuda.so.1
/usr/lib/i386-linux-gnu/libcuda.so
/usr/lib/x86_64-linux-gnu/libcuda.so.1
/usr/lib/x86_64-linux-gnu/libcuda.so

```
Would not be at all surprised if none of them exist any longer as the system does it's job well... will not hurt to check and verify.

And speaking of verify:
On our 'unity' warning; what returns:
```

ls -al /etc/compizconfig/upgrades

```
Let's look and see if there might be something to be concerned about.

[INDENT][INDENT]clean as a whistle - just like we want it
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-01
Alright so there is nothing left indeed.

```
~$ ls -al /etc/compizconfig/upgrades
-rw-r--r-- 1 root root   84 Jun 12  2013 com.canonical.unity.unity.01.upgrade
-rw-r--r-- 1 root root  159 Jun 12  2013 com.canonical.unity.unity.02.upgrade
```

---

### Post by Bashing-om on 2015-03-01
chris137; Well. well !

I think now we are all done !
Let us rest on our laurels and see if there are now any graphics issues .

[INDENT][INDENT]dirty jobs done
[INDENT][INDENT][INDENT]dirt cheap
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-01
Wow, thanks for your help!
Is it possible to give some kind of likes or rating?
Really appreciate you helping me!

Let's see if there will be a crash in a few days or flickering starts again.

---

### Post by Bashing-om on 2015-03-01
chris137; Aww shucks,


Anything ya want to critique ? Anything we did that you do not understand ?
Lesson 1 learned, keep the vbox updated when updating the install's kernel ! And always clean up behind !


Just hang out here and pass it on down the line... help others with your experience.

This is open source at it's best, it's
[INDENT][INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-01
Everything was fine! I sometimes did Not understand your english perfectly but that is just an issue I have to deal with as a non-native speaker.

Yeah, cleaning up is Not my specialty.
But I See now that it is clever to Do so.

And wow, was it a pain to write this Post on my phone... 'didn't you mean this or that? Lol, Don't care that you wanna write in english"

Thanks again for your help!

---

### Post by Bashing-om on 2015-03-01
chris137; Hey :

Your English is so good I did not realize you would have a problem with my vernacular or use of American slang to express myself.
Excuse me .

And was glad to help; you are quite welcome. just pass it on down the line.

Maybe YES, this is all said and done with ... Time will tell.

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-02
Well..
After booting today linux would not start. I got the ubuntu-logo loading but after a few seconds it just stops. I then also don't get into a tty.
I have to reboot to get into the tty before ubuntu stops loading. Then I have normal access to my system.
Der seems to be an issue with the driver again. Lightdm won't start.
I tried reinstalling the drivers which sadly had no effect (even tried a newer version this time too).
I'm not sure if I have the energy to experiment there any longer and think about reinstalling.
Luckily I got my Windows up and running a few days ago but that's really no alternative. Sucks already.

Any quick ideas on how to proceed? I honestly did not put too much effort in thinking on my own because I'm still pretty pissed by all problems this card brought me.

---

### Post by dino99 on 2015-03-02
hi chris,
i'm a 750ti user too since about 6 months, and without trouble on either utopic/vivid i386
the driver used is from xorg-edgers ppa (the more stable i've found along the time)
here there is no xorg.conf: not needed anymore with actual ubuntu (not sure about Precise) except for multi-monitor. (xorg.conf is too often to be blamed if not perfectly set)
As i've read that you are using LTS, i have to tell that i have never had luck trying to use the backported packages (all borked and conflicting most of the time)
Vivid is way more stable than that LTS

only my two cents ):P

---

### Post by chris137 on 2015-03-02
I think xorg-edgers got mentioned along the way somewhere.
Acutally I do use multiple monitors. Will that not be working at all or just with a xorg.conf?

---

### Post by dino99 on 2015-03-02
for multi monitors on the same system, then set the config with nvidia-settings

---

### Post by chris137 on 2015-03-02
Theoretically that should be working with the driver I downloaded from nvidia.
Well.. It doesn't. 

I don't want to reinstall, I don't want to look for the issue for hours and I don't want to use Windows.
I guess TV it is..

---

### Post by Bashing-om on 2015-03-02
chris137; Shucks;

What a way to start my day ! I "thought" this was behind, over and done with.

OK, Let's take a quick look/check.
1st. can you boot to a terminal, from there we can have that looksee:
Boot to grub's boot menu, 'e' key for edit mode -> boot parameters screen;
arrow down to the line similar " linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff " arrow across to the term "quiet splash" and replace these terms with "text" - without the quotes;
key combo ctl+x to continue the boot process to TTY1.
login here with user name and pass word, no response to the screen when password is entered - normal.

What returns from terminal commands:
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home
ls -al /home/chris

```
where 'chris' is your normal user name on the system. IF all comes back as "you", let's start the GUI from terminal and see if any errors are reported:
```

sudo service lightdm start

```

To return to TTY1 key combo ctl+alt+F1
GUI key combo ctl+alt+F7
To restart the system:
```

sudo shutdown -r now

```

[INDENT][INDENT]again, just goes to show
[INDENT][INDENT][INDENT]never can tell
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-02
Didn't manage to send the results a few hours ago, had to go.
I skipped the boot parameters since I figured this would be only to get the tty. That is possible without modifying the boot params.
Took a picture of the results since it seemed easier.
[https://www.dropbox.com/s/t1tc8lxisiji8t1/2015-03-02%2017.20.55.jpg?dl=0](https://www.dropbox.com/s/t1tc8lxisiji8t1/2015-03-02%2017.20.55.jpg?dl=0)
My home-directory is pretty stuffed so I didn't include it. What exactly are you looking for there?
As you can see lightdm obviously has an issue.
/var/log/lightdm/lightdm.log looks like this
```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.10.4, UID=0 PID=1924
[+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Registered seat module unity
[+0.00s] DEBUG: Registered seat module surfaceflinger
[+0.01s] DEBUG: Adding default seat
[+0.01s] DEBUG: Seat: Starting
[+0.01s] DEBUG: Seat: Creating user session
[+0.03s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.03s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+0.06s] DEBUG: Seat: Creating display server of type x
[+0.07s] DEBUG: Deactivating Plymouth
[+0.09s] DEBUG: Using VT 7
[+0.09s] DEBUG: Seat: Starting local X display on VT 7
[+0.09s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.09s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.09s] DEBUG: DisplayServer x-0: Launching X Server
[+0.09s] DEBUG: Launching process 2004: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.09s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.09s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.09s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.09s] DEBUG: Process 2004 exited with return value 1
[+0.09s] DEBUG: DisplayServer x-0: X server stopped
[+0.09s] DEBUG: Releasing VT 7
[+0.09s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+0.09s] DEBUG: Quitting Plymouth
[+6.23s] DEBUG: Seat: Display server stopped
[+6.23s] DEBUG: Seat: Stopping session
[+6.23s] DEBUG: Seat: Session stopped
[+6.23s] DEBUG: Seat: Stopping display server, no sessions require it
[+6.23s] DEBUG: Seat: Active display server stopped, starting greeter
[+6.23s] DEBUG: Seat: Creating greeter session
[+6.23s] DEBUG: Seat: Creating display server of type x
[+6.23s] DEBUG: Using VT 7
[+6.23s] DEBUG: Seat: Starting local X display on VT 7
[+6.23s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+6.23s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+6.23s] DEBUG: DisplayServer x-0: Launching X Server
[+6.23s] DEBUG: Launching process 5808: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+6.23s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+6.23s] DEBUG: Got signal 15 from process 1
[+6.23s] DEBUG: Caught Terminated signal, shutting down
[+6.23s] DEBUG: Stopping display manager
[+6.23s] DEBUG: Seat: Stopping
[+6.23s] DEBUG: Seat: Stopping display server
[+6.23s] DEBUG: Sending signal 15 to process 5808
[+6.23s] DEBUG: Seat: Stopping session
[+6.23s] DEBUG: Seat: Session stopped
[+6.23s] DEBUG: Process 5808 terminated with signal 15
[+6.23s] DEBUG: DisplayServer x-0: X server stopped
[+6.23s] DEBUG: Releasing VT 7
[+6.23s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+6.23s] DEBUG: Seat: Display server stopped
[+6.23s] DEBUG: Seat: Stopped
[+6.23s] DEBUG: Display manager stopped
[+6.23s] DEBUG: Stopping daemon
[+6.24s] DEBUG: Exiting with return value 0
```
I mounted the linux-partition on windows so it's easier to retrieve log-files and view the directory-indexes.

---

### Post by Bashing-om on 2015-03-02
chris137; Well, ...

Not something easy like authorization and permissions.
Access rights are good. Which was my 1st thought that these rights had been altered.
> 
My home-directory is pretty stuffed so I didn't include it. What exactly are you looking for there?

Just looking that "you" are the owner and group of the files in your /home directory ( except a few that you do know otherwise). I will bet that it is not an issue.

I am not all that familiar with 'lightdm' but we could take some stabs in the dark and see what results.
1st though, let's see what the log file in your /home directory relates to the condition:
```

cat /home/chris/.xsession-errors

```

If you can function in a terminal or console, that means the problem must be in the Xserver layer.

[INDENT][INDENT][INDENT]and a hunt'n we will go
[/INDENT][/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-02
```
script for ibus unter run_im started.
script for auto unter run_im started.
script for default unter run_im started.
init: at-spi2-registryd-main-process stopped, will be restarted
init: at-spi2-registryd-main-process stopped, will be restarted
init: at-spi2-registryd-main-process stopped, will be restarted
init: at-spi2-registryd-main-process stopped, will be restarted
init: at-spi2-registryd-main-process stopped, will be restarted
init: at-spi2-registryd-main-process stopped, will be restarted
init: at-spi2-registryd-main-process stopped, will be restarted
init: at-spi2-registryd-main-process stopped, will be restarted
init: at-spi2-registryd-main-process stopped, will be restarted
init: at-spi2-registryd-main-process stopped, will be restarted
init: restart of at-spi2-registryd too fast, interrupted
init: unity-settings-daemon-main-process(3106) exited with status 1
init: hud-main-process(3111) exited with status 1
init: gnome-session (Unity)-main-process(3115) exited with status 1
init: unity-panel-service-main-process(3122) exited with status 1
init: indicator-printers-main-process(3375) exited with status 1
init: indicator-bluetooth-main-process(3359) stopped by TERM-Signal
init: indicator-power-main-process(3362) stopped by TERM-Signal
init: indicator-datetime-main-process(3367) stopped by TERM-Signal
init: indicator-session-main-process(3384) stopped by TERM-Signal
init: indicator-application-main-process(3402) stopped by TERM-Signal
init: Disconnected from notified D-Bus bus
```
Log was partly German, translated as best as I could.

Edit: While browsing through home I found .nvidia-settings.rc which lies there untouched since 2 weeks (so since the first install)
Looks like that:
```
#
# /home/chris/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Wed Feb 18 01:16:57 2015
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = Yes
UpdateRulesOnProfileNameChange = Yes
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000
Timer = Thermal_Monitor_(GPU_0),Yes,1000
Timer = Memory_Used_(GPU_0),Yes,3000

# Attributes:

0/SyncToVBlank=1
0/LogAniso=0
0/FSAA=0
0/TextureSharpen=0
0/TextureClamping=1
0/FXAA=0
0/AllowFlipping=1
0/FSAAAppControlled=1
0/LogAnisoAppControlled=1
0/OpenGLImageSettings=1
0/FSAAAppEnhanced=0
0/XVideoSyncToDisplayID=VGA-0
[DPY:VGA-0]/Dithering=0
[DPY:VGA-0]/DitheringMode=0
[DPY:VGA-0]/DitheringDepth=0
[DPY:VGA-0]/SynchronousPaletteUpdates=0
[DPY:DVI-D-0]/RedBrightness=0.000000
[DPY:DVI-D-0]/GreenBrightness=0.000000
[DPY:DVI-D-0]/BlueBrightness=0.000000
[DPY:DVI-D-0]/RedContrast=0.000000
[DPY:DVI-D-0]/GreenContrast=0.000000
[DPY:DVI-D-0]/BlueContrast=0.000000
[DPY:DVI-D-0]/RedGamma=1.000000
[DPY:DVI-D-0]/GreenGamma=1.000000
[DPY:DVI-D-0]/BlueGamma=1.000000
[DPY:DVI-D-0]/Dithering=0
[DPY:DVI-D-0]/DitheringMode=0
[DPY:DVI-D-0]/DitheringDepth=0
[DPY:DVI-D-0]/DigitalVibrance=0
[DPY:DVI-D-0]/ColorSpace=0
[DPY:DVI-D-0]/ColorRange=0
[DPY:DVI-D-0]/SynchronousPaletteUpdates=0
[DPY:HDMI-0]/RedBrightness=0.000000
[DPY:HDMI-0]/GreenBrightness=0.000000
[DPY:HDMI-0]/BlueBrightness=0.000000
[DPY:HDMI-0]/RedContrast=0.000000
[DPY:HDMI-0]/GreenContrast=0.000000
[DPY:HDMI-0]/BlueContrast=0.000000
[DPY:HDMI-0]/RedGamma=1.000000
[DPY:HDMI-0]/GreenGamma=1.000000
[DPY:HDMI-0]/BlueGamma=1.000000
[DPY:HDMI-0]/Dithering=0
[DPY:HDMI-0]/DitheringMode=0
[DPY:HDMI-0]/DitheringDepth=0
[DPY:HDMI-0]/DigitalVibrance=0
[DPY:HDMI-0]/ColorSpace=0
[DPY:HDMI-0]/ColorRange=0
[DPY:HDMI-0]/SynchronousPaletteUpdates=0
[DPY:DVI-D-1]/RedBrightness=0.000000
[DPY:DVI-D-1]/GreenBrightness=0.000000
[DPY:DVI-D-1]/BlueBrightness=0.000000
[DPY:DVI-D-1]/RedContrast=0.000000
[DPY:DVI-D-1]/GreenContrast=0.000000
[DPY:DVI-D-1]/BlueContrast=0.000000
[DPY:DVI-D-1]/RedGamma=1.000000
[DPY:DVI-D-1]/GreenGamma=1.000000
[DPY:DVI-D-1]/BlueGamma=1.000000
[DPY:DVI-D-1]/Dithering=0
[DPY:DVI-D-1]/DitheringMode=0
[DPY:DVI-D-1]/DitheringDepth=0
[DPY:DVI-D-1]/DigitalVibrance=0
[DPY:DVI-D-1]/ColorSpace=0
[DPY:DVI-D-1]/ColorRange=0
[DPY:DVI-D-1]/SynchronousPaletteUpdates=0
```
Not sure if relevant or helpful at all but I thought I better include it.

---

### Post by Bashing-om on 2015-03-02
chris137; Humm ...

Ya got me in a learning mode once more.
Maybe: poke .
What results with terminal command:
```

nvidia-settings --load-config-only

```
Let's see if that starts the GUI.

[INDENT][INDENT]this too is one of those times
[INDENT][INDENT][INDENT][INDENT]I do wonder
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-02
```
~$ nvidia-settings --load-config-only
ERROR: The control display is undefined; please run `nvidia-settings --help` for usage information.

~$ sudo nvidia-settings --load-config-only
XDG_RUNTIME_DIR not set in the environment
ERROR: The control display is undefined; please run `nvidia-settings --help` for usage information.
```
The additional error with sudo is probably caused by running it as sudo, not by the driver, correct?

---

### Post by Bashing-om on 2015-03-02
chris137; Welp;

Disappointed that the GUI did not start.
Yeah I tend to agree that 'sudo' here is a miss-application ... NEVER ever never run elevated privileges with any file in your /home directory. There you are the supreme authority. Running 'sudo' there can and does have some undesirable side effects.
Check .Xauthority and .ICEauthority again that those access are not now changed.

And from the .Xsession-errors log, I tend to think that what we have here is the driver config issue.

I "think" we need to -somehow - start nvidia-settings utility and check what is set there and then RE-save those settings.
Maybe RE-install nvidia-settings ??? I will consider that option.

What info can we get:
```

gksu nvidia-settings

```
As we have no GUI started, I will not be surprised if the command fails. Of interest then is the errors reported .

And as I am curious, what results if we take the given directive:
```

nvidia-settings --help

```
here I am prepared to be surprised in that we may get some relevant help.

[INDENT][INDENT]back up 2 yards
[INDENT][INDENT][INDENT]and punt
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-02
Nothing changed with .Xauthority or .ICEauthority
```
~$ gksu nvidia-settings
(gksu:7500): Gtk-WARNING **: cannotopen display:
```

Here is nvidia-settings --help:
[http://paste.ubuntu.com/10507003/](http://paste.ubuntu.com/10507003/)

---

### Post by Bashing-om on 2015-03-02
chris137; Well ....

Not much help there ...
> 
(gksu:7500): Gtk-WARNING **: cannotopen display:

pretty much ambiguous - not much there.

Let see if we can indeed isolate to a driver issue:
try and restart the system with the boot parameter "nomodeset" (add nomodeset after "quiet splash" in grub's boot parameters screen).

If the GUI starts now we know it is a driver issue.

[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-02
As it turns out that was already set.
Probably edited the grub.conf instead of editing it temporarily and then forgot about it.
I removed it just to try but no change there.

---

### Post by Bashing-om on 2015-03-02
chris137; Think'n

The boot parameter "nomodeset" disables Kernel Mode Setting. Thinking how it being set all this time could effect.

What results now when booting with out that parameter ?

[INDENT][INDENT]where to poke at next ?
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-02
As above I actually thought there was no difference.. Obviously didn't apply the changes or anything.
Because after you asked I just looked again to confirm it and now it does not start at all.
No ubuntu-logo, just a black screen.

---

### Post by Bashing-om on 2015-03-02
chris137; Sheessshh ...

A black screen is generally graphics driver related.
Can you boot to the login screen ?

Maybe we can see what results when we re-configure lightdm (??) .

[INDENT][INDENT]just do not know
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-02
I only got these two options:
Start without nomodeset which leads to a black screen. No tty, no boot-logo or anything.
Or I start with nomodeset which brings me a tty (or gets stuck at the logo if I don't change to the tty fast enough).
And there you know what I can do.
Tried a dpkg-reconfigure lightdm but that did not help.
Maybe a complete reinstall? Found this command which looks like achieving it.
sudo apt-get install --*reinstall lightdm*

---

### Post by Bashing-om on 2015-03-02
chris137; Yeah;

But, maybe; just
Maybe some fault in the saved user-session.
Let's try this:
```

rm ~/.dmrc

```
Re-boot, see if that has an effect.
Will not hurt a thing to try and RE-install lightdm .. might get some more info.

[INDENT][INDENT]keep on 'til something gives
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-02
.dmrc only said
[Desktop]Session=ubuntu
deleted it anyway but had no effect.

Also reinstalling lightdm with the command above did not change anything.
Even purged and then installed it - no change.
.dmrc got not created during the process btw.

---

### Post by Bashing-om on 2015-03-02
chris137; Next !
```

You could try resetting lightdm and the 'greeter' by logging in to a virtual terminal (Ctrl-Alt-F1...F6) and then doing

sudo service lightdm stop
sudo dpkg-reconfigure lightdm 
sudo dpkg-reconfigure unity-greeter 
sudo service lightdm start

```

[INDENT][INDENT]stepping up  ladder
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-02
No effect either.
Something I already saw before:
When starting lightdm two times right after another (after the first time it won't start as said above) it claims to run.
Also service lightdm status claims it's running.
However no luck on F7 and lightdm.log also reads exited with status 1 (or sth like that - mentioned above too).

---

### Post by Bashing-om on 2015-03-02
chris137; poke'n .


If 'lightdm' is runnable;
Try:
```

sudo apt-get install --reinstall unity

```

To be honest, still holding my breath that it is related to the graphics driver .

---

### Post by chris137 on 2015-03-02
No luck with that either.
Probably because lightdm is not really runnable.
As said it reports it would be but ps aux does not show it either.

So.. If you have no real idea where this solution-seeking is headed right now I'll probably reinstall ubuntu tomorrow.
It actually is tomorrow already so I won't be online much longer anyway - screw timezones..

---

### Post by Bashing-om on 2015-03-02
chris137;


The sledge hammer:
```

sudo apt-get install --reinstall ubuntu-desktop

```
As no I still do not know what is not going on.

---

### Post by chris137 on 2015-03-02
No luck again.
This also was the last time I booted up linux for today. Don't forget I'm 7h ahead :D

---

### Post by Bashing-om on 2015-03-02
chris137; Hey;

> **chris137 said:**
> No luck again.
This also was the last time I booted up linux for today. Don't forget I'm 7h ahead :D

comes a time one has to take a break for sanity's sake.
What ever you decide. But, I am here for the long haul.

[INDENT][INDENT]can't never did nothing
[/INDENT][/INDENT]

---

### Post by chris137 on 2015-03-04
So since it did not look like we would get to the solution anytime soon I reinstalled ubuntu yesterday.
Copied the files that I need and that's it. A good cleanup was probably what I needed. I'm at 10GB right now whereas the previous installation ate up more than double over time.

Well.. 100 posts for nothing?
Not quite. Learned much from the process.
Just a shame we didn't reach the finish line.

Thanks again to Bashing-om for your never ending patience ;)

---

### Post by Bashing-om on 2015-03-04
chris137; Hey;

Like you I would have liked to learn the causation ! The nuclear solution is always an option and though we did not learn much, we did learn a bit.

As this is now at an end;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

