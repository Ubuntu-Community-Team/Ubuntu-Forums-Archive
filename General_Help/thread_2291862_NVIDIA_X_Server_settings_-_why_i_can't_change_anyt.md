---
title: "NVIDIA X Server settings - why i can't change anything?"
date: 2015-08-23
forum: General Help
---

### Post by jankupisz on 2015-08-23
Hi, i have problem with Nvidia X Server setting...

i can't change any settings there because it look like that:
[http://scr.hu/1k0r/r21cq](http://scr.hu/1k0r/r21cq)

I'm using NVIDIA binary driver - version 346.82 nvidia-346-updates (official nvidia):
[http://scr.hu/1k0r/lb4rn](http://scr.hu/1k0r/lb4rn)

When i close X Server settings in terminal i can see:
[http://scr.hu/1k0r/dosjx](http://scr.hu/1k0r/dosjx)

When i use command [COLOR=#000000][FONT=Ubuntu Mono]dpkg -l | grep nvidia [/FONT][/COLOR] i can see:
[http://scr.hu/1k0r/zak36](http://scr.hu/1k0r/zak36)

What is wrong with my computer? ;( could anyone help me?

---

### Post by grahammechanical on 2015-08-23
Do you want my guess? And it is only a guess.

The first screenshot is what the Nvidia Xserver settings utility looks like when we have the Nvidia settings utility installed but are not using an Nivida driver. Does that machine have Nvida Optimus technology? Have you at some point installed Bumblebee?

We may also get this effect if we have installed an Nvidia driver from the Nvidia web site and then attempted to remove it but have not actually purged it. I personally have seen Additional Drivers get very confused about the actual driver in use when I tried to install an Nvidia driver from the web site that did not support my graphic adapter and so would not build a kernel module for the driver. And that is when I saw the Nvidia Xserver settings utility with the reduced functions.

Try using the open source video driver and doing a couple of restarts and then switching to a Nvdia driver and then see what the Nvdia Xserver settings utility is offering you.

Regards.

---

### Post by jankupisz on 2015-08-23
I installed Bumblebee few months ago, but i don't know i have it now because when i install that new drivers there is something in terminal about automatic delete it? how i could check that i have nvidia optimus technology? I really like ubuntu, but some things are to hard for me and they are harder if i can't find anything about my problems like that time... I installed that drivers from repository. So what is the best in that situation firstly to do? Because i tried yesterday opensource drivers 355.06 but my screen was black and i need to install by recovery mode older drivers  because i can't change it...

---

### Post by Bashing-om on 2015-08-23
jankupisz; Hi !

As a place to start, let's identify the hardware.
```

lspci -vnn | grep VGA -A 12
sudo lshw -C display

```
How then long ago did you install BumbleBee ? A PPA ?
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

And what drivers are presently installed ?
```

dpkg -l | grep -i nvidia

```

I look to cleaning up the system of old drivers, and BumbleBee ( nvidia-prime is now recommended ) and install the recommended graphics driver.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by jankupisz on 2015-08-23
Hardware: [http://scr.hu/1k0r/0lf62](http://scr.hu/1k0r/0lf62)
Your next question: [http://scr.hu/1k0r/njhxt](http://scr.hu/1k0r/njhxt) and [http://scr.hu/1k0r/dsj2q](http://scr.hu/1k0r/dsj2q) and [http://scr.hu/1k0r/63o1g](http://scr.hu/1k0r/63o1g)
 and [http://scr.hu/1k0r/63o1g](http://scr.hu/1k0r/63o1g) and [http://scr.hu/1k0r/vlbu8](http://scr.hu/1k0r/vlbu8)

Last one: [http://scr.hu/1k0r/uo4br](http://scr.hu/1k0r/uo4br)

What i need to do when we have that answers?

---

### Post by Bashing-om on 2015-08-23
jankupisz; Hey, hey;

Working from screenshots is cumbersome and difficult, please use code blocks within the thread:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Due to my ignorance, I do not see the Nvidia hardware in the output. Need to come up with the proper command to look at at this type of hardware. Humm ...

Also we need to know what modules that are installed as indicated from the terminal command:
```

dpkg -l | grep -i nvidia

```

Release 14.04 now has drivers for later versions of Nvidia, presently you -DO- have a conflict in driver sources.
a) mamarley PPA
b) xorg-edgets
I would expect we can do away with both, and use the proprietary drivers available in our software repository. Take the easy way out.

Until I know better
[INDENT][INDENT][INDENT]this is the best I can do
\[/INDENT][/INDENT][/INDENT]

---

### Post by jankupisz on 2015-08-23
```
jasiek@jasiek-SATELLITE-L50-A:~$ **lspci -vnn | grep VGA -A 12**
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device [1179:fa47]
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915


00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
    Subsystem: Toshiba America Info Systems Device [1179:fa49]
    Flags: bus master, fast devsel, latency 0, IRQ 45
```

```
jasiek@jasiek-SATELLITE-L50-A:~$** sudo lshw -C display**
[sudo] password for jasiek: 
  *-display               
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)
```


```
jasiek@jasiek-SATELLITE-L50-A:~$ **cat -n /etc/apt/sources.list**
     1    # deb cdrom:[Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://pl.archive.ubuntu.com/ubuntu/ trusty main restricted
     6    deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://pl.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    11    deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://pl.archive.ubuntu.com/ubuntu/ trusty universe
    17    deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty universe
    18    deb http://pl.archive.ubuntu.com/ubuntu/ trusty-updates universe
    19    deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://pl.archive.ubuntu.com/ubuntu/ trusty multiverse
    27    deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty multiverse
    28    deb http://pl.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    29    deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://pl.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    37    deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu trusty-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
    41    deb http://security.ubuntu.com/ubuntu trusty-security universe
    42    deb-src http://security.ubuntu.com/ubuntu trusty-security universe
    43    deb http://security.ubuntu.com/ubuntu trusty-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu trusty partner
    51    # deb-src http://archive.canonical.com/ubuntu trusty partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu trusty main
    56    deb-src http://extras.ubuntu.com/ubuntu trusty main
```


```
jasiek@jasiek-SATELLITE-L50-A:~$ **tail -v -n +1 /etc/apt/sources.list.d/***
==> /etc/apt/sources.list.d/caffeine-developers-caffeine-dev-trusty.list <==
deb http://ppa.launchpad.net/caffeine-developers/caffeine-dev/ubuntu trusty main
# deb-src http://ppa.launchpad.net/caffeine-developers/caffeine-dev/ubuntu trusty main


==> /etc/apt/sources.list.d/caffeine-developers-caffeine-dev-trusty.list.save <==
deb http://ppa.launchpad.net/caffeine-developers/caffeine-dev/ubuntu trusty main
# deb-src http://ppa.launchpad.net/caffeine-developers/caffeine-dev/ubuntu trusty main


==> /etc/apt/sources.list.d/danjaredg-jayatana-trusty.list <==
deb http://ppa.launchpad.net/danjaredg/jayatana/ubuntu trusty main
# deb-src http://ppa.launchpad.net/danjaredg/jayatana/ubuntu trusty main


==> /etc/apt/sources.list.d/danjaredg-jayatana-trusty.list.save <==
deb http://ppa.launchpad.net/danjaredg/jayatana/ubuntu trusty main
# deb-src http://ppa.launchpad.net/danjaredg/jayatana/ubuntu trusty main


==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/linrunner-tlp-trusty.list <==
deb http://ppa.launchpad.net/linrunner/tlp/ubuntu trusty main
# deb-src http://ppa.launchpad.net/linrunner/tlp/ubuntu trusty main
# deb-src http://ppa.launchpad.net/linrunner/tlp/ubuntu trusty main


==> /etc/apt/sources.list.d/linrunner-tlp-trusty.list.save <==
deb http://ppa.launchpad.net/linrunner/tlp/ubuntu trusty main
# deb-src http://ppa.launchpad.net/linrunner/tlp/ubuntu trusty main
# deb-src http://ppa.launchpad.net/linrunner/tlp/ubuntu trusty main


==> /etc/apt/sources.list.d/mamarley-nvidia-trusty.list <==
deb http://ppa.launchpad.net/mamarley/nvidia/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mamarley/nvidia/ubuntu trusty main


==> /etc/apt/sources.list.d/openambit-ppa-trusty.list <==
deb http://ppa.launchpad.net/openambit/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/openambit/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/openambit/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/openambit/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/openambit-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/openambit/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/openambit/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/openambit/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/openambit/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_create-launcher_ubuntu.list <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/create-launcher/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_create-launcher_ubuntu.list.save <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/create-launcher/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf


==> /etc/apt/sources.list.d/tualatrix-ppa-trusty.list <==
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/tualatrix-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list <==
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/webupd8team-java-trusty.list <==
deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main


==> /etc/apt/sources.list.d/webupd8team-java-trusty.list.save <==
deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main


==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list <==
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
```


```
jasiek@jasiek-SATELLITE-L50-A:~$ **dpkg -l | grep -i nvidia**
ii  bbswitch-dkms                                 0.7-2ubuntu1                                        amd64        Interface for toggling the power on nVidia Optimus video cards
ii  bumblebee                                     3.2.1-9~gpu14.04.1                                  amd64        NVIDIA Optimus support for Linux
ii  bumblebee-nvidia                              3.2.1-9~gpu14.04.1                                  amd64        NVIDIA Optimus support using the proprietary NVIDIA driver
rc  libcuda1-304                                  304.125-0ubuntu1~xedgers14.04.1                     amd64        NVIDIA CUDA runtime library
rc  libcuda1-340                                  340.76-100ubuntu100~ppa3~trusty0                    amd64        NVIDIA CUDA runtime library
rc  libcuda1-340-updates                          340.76-0ubuntu0.1                                   amd64        NVIDIA CUDA runtime library
ii  libcuda1-346-updates                          346.82-0ubuntu0.2                                   amd64        NVIDIA CUDA runtime library
rc  libcuda1-352                                  352.30-100ubuntu100~ppa0~trusty0                    amd64        NVIDIA CUDA runtime library
rc  libcuda1-355                                  355.06-0ubuntu0~xedgers14.04.1                      amd64        NVIDIA CUDA runtime library
rc  nvidia-340                                    340.76-0ubuntu1~xedgers14.04.4                      amd64        NVIDIA binary driver - version 340.76
ii  nvidia-346-updates                            346.82-0ubuntu0.2                                   amd64        NVIDIA binary driver - version 346.82
rc  nvidia-352                                    352.30-100ubuntu100~ppa0~trusty0                    amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-libopencl1-346-updates                 346.82-0ubuntu0.2                                   amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-libopencl1-352                         352.30-100ubuntu100~ppa0~trusty0                    amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-opencl-icd-340                         340.76-100ubuntu100~ppa3~trusty0                    amd64        NVIDIA OpenCL ICD
ii  nvidia-opencl-icd-346-updates                 346.82-0ubuntu0.2                                   amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-352                         352.30-100ubuntu100~ppa0~trusty0                    amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                               355.06-100ubuntu100~ppa0~trusty0                    amd64        Tool for configuring the NVIDIA graphics driver
ii  primus                                        0~20131127-2                                        amd64        client-side GPU offloading for NVIDIA Optimus
```

No problem, here you have code :) now you know more about my problem? how i could make cleanup in that mess? :(

---

### Post by Bashing-om on 2015-08-23
jankupisz; K ;

Much much better in code blocks. Thanks !

OK. Yeah there is clean up to be done. Before we proceed with the cleanup; let's look at what the system offers for a graphics driver.
```

sudo ubuntu-drivers devices
sudo ubuntu-drivers list

```
When we know what we are working toward, we ppa-purge the graphics PPAs, comment the source fetchs out in the sources.list.d file, purge the present drivers. And then finally install the driver from our repository.

Once we know what we are going to do
[INDENT][INDENT][INDENT]then just do it .
[/INDENT][/INDENT][/INDENT]

Sorry about the delay in my response, was interrupted and just now posting this reply.

---

### Post by jankupisz on 2015-08-23
I am very grateful that you try to help me... time is not a problem. Thank your really much for that ;)

```
jasiek@jasiek-SATELLITE-L50-A:~$ **sudo ubuntu-drivers devices**[sudo] password for jasiek: 
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001292sv00001179sd0000FA47bc03sc02i00
model    : GK208M [GeForce GT 740M]
vendor   : NVIDIA Corporation
driver   : nvidia-355 - third-party free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-346-updates - distro non-free
driver   : nvidia-340-updates - distro non-free
driver   : nvidia-346 - third-party free
driver   : nvidia-340 - third-party free
```

```
jasiek@jasiek-SATELLITE-L50-A:~$ **sudo ubuntu-drivers list**
nvidia-340-updates
nvidia-340
nvidia-346-updates
nvidia-355
nvidia-346
```

---

### Post by Bashing-om on 2015-08-23
jankupisz; Outstanding !

We have the hardware identified. We know that the repository supports that hardware. Now it is but a matter of cleaning up and installing the driver from our repository.
```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:mamarley/nvidia
sudo ppa-purge ppa:ubuntu-x-swat/x-updates
sudo apt-get purge nvidia-*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```

I personally prefer to keep modifications available that I have made - adding comments as to what and why I am doing this -  And rather then remove the PPA entries, let's comment them out to make them in-effective.
Fire up your favorite text editor ( gedit ?) and simply add the comment (#) character at the start of the line(s) such that they are not parsed when the file is executed.
```

gksu gedit /etc/apt/sources.list.d/mamarley-nvidia-trusty.list

```
comment out the line " deb [http://ppa.launchpad.net/mamarley/nvidia/ubuntu](http://ppa.launchpad.net/mamarley/nvidia/ubuntu) trusty main "

Repeat for the xorg-edgers PPA:
```

gksu gedit /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list

```
comment out the line " deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) trusty main "
Save the files and exit back to terminal.
- It is possible that you have not installed the 'gksu' tool - advise please if this is case and you need advise on installing it.

Next is to insure the system is fully updated:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
'dist-upgrade' has nothing to be with a release upgrade to the next version. 'dist-upgrade' only updates installed packages on the present 'distibution' .

OK now for installing the graphics driver:
```

sudo ubuntu-drivers autoinstall

```
Here I do expect the system to choose to install the 346 version.
Cheap insurance is to have the system generate once more a new "/etc/X11/xorg.conf" config file.
```

sudo nvidia-xconfig

```

Now restart the system so that the Nvidia driver can take effect.

There is now the utility 'nvidia-settings' - installed by default when the nvidia proprietary driver is installed - to switch between the graphics chip sets.

[INDENT][INDENT]I do expect all to be
[INDENT][INDENT][INDENT]finer than a frog's hair
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jankupisz on 2015-08-23
What i need to choose? change?

```
jasiek@jasiek-SATELLITE-L50-A:~$ [B]sudo ppa-purge ppa:mamarley/nvidia
[/B]Updating packages lists
PPA to be removed: mamarley nvidia
Package revert list generated:
 bumblebee/trusty bumblebee-nvidia/trusty libvdpau1:amd64/trusty 
nvidia-settings/trusty vdpauinfo/trusty


Disabling mamarley PPA from /etc/apt/sources.list.d/mamarley-nvidia-trusty.list
Updating packages lists
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
libvdpau1 jest ju&#380; w najnowszej wersji.
Wybrano wersj&#281; "3.2.1-5+xedgers14.04.1" (xorg-edgers fresh X crack:14.04/trusty [amd64]) pakietu "bumblebee"
Wybrano wersj&#281; "3.2.1-5+xedgers14.04.1" (xorg-edgers fresh X crack:14.04/trusty [amd64]) pakietu "bumblebee-nvidia"
Wybrano wersj&#281; "1.1-0ubuntu1~xedgers14.04.1" (xorg-edgers fresh X crack:14.04/trusty [amd64]) pakietu "libvdpau1"
Wybrano wersj&#281; "355.06-0ubuntu0~xedgers14.04.1" (xorg-edgers fresh X crack:14.04/trusty [amd64]) pakietu "nvidia-settings"
Wybrano wersj&#281; "0.1-1" (Ubuntu:14.04/trusty [amd64]) pakietu "vdpauinfo"
Nast&#281;puj&#261;ce pakiety zosta&#322;y zainstalowane automatycznie i nie s&#261; ju&#380; wi&#281;cej wymagane:
  linux-headers-generic-lts-utopic linux-image-generic-lts-utopic
Aby je usun&#261;&#263; nale&#380;y u&#380;y&#263; "apt-get autoremove".
Zostan&#261; zainstalowane STARE wersje nast&#281;puj&#261;cych pakietów:
  bumblebee bumblebee-nvidia nvidia-settings vdpauinfo
0 aktualizowanych, 0 nowo instalowanych, 4 cofni&#281;tych wersji, 0 usuwanych i 1 nieaktualizowanych.
Konieczne pobranie 53,4 kB/920 kB archiwów.
Po tej operacji zostanie zwolnione 516 kB miejsca na dysku.
Kontynuowa&#263;? [T/n] t
Pobieranie:1 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main bumblebee amd64 3.2.1-5+xedgers14.04.1 [45,3 kB]
Pobieranie:2 http://pl.archive.ubuntu.com/ubuntu/ trusty/universe vdpauinfo amd64 0.1-1 [8084 B]
Pobrano 53,4 kB w 0s (95,0 kB/s)                                      
dpkg: ostrze&#380;enie: zast&#261;pienie nvidia-settings w wersji 355.06-100ubuntu100~ppa0~trusty0 wcze&#347;niejsz&#261; wersj&#261; 355.06-0ubuntu0~xedgers14.04.1
(Odczytywanie bazy danych ... 629908 plików i katalogów obecnie zainstalowanych.)
Preparing to unpack .../nvidia-settings_355.06-0ubuntu0~xedgers14.04.1_amd64.deb ...
Unpacking nvidia-settings (355.06-0ubuntu0~xedgers14.04.1) over (355.06-100ubuntu100~ppa0~trusty0) ...
dpkg: ostrze&#380;enie: zast&#261;pienie bumblebee-nvidia w wersji 3.2.1-9~gpu14.04.1 wcze&#347;niejsz&#261; wersj&#261; 3.2.1-5+xedgers14.04.1
Preparing to unpack .../bumblebee-nvidia_3.2.1-5+xedgers14.04.1_amd64.deb ...
Unpacking bumblebee-nvidia (3.2.1-5+xedgers14.04.1) over (3.2.1-9~gpu14.04.1) ...
dpkg: ostrze&#380;enie: zast&#261;pienie bumblebee w wersji 3.2.1-9~gpu14.04.1 wcze&#347;niejsz&#261; wersj&#261; 3.2.1-5+xedgers14.04.1
Preparing to unpack .../bumblebee_3.2.1-5+xedgers14.04.1_amd64.deb ...
bumblebeed stop/waiting
Unpacking bumblebee (3.2.1-5+xedgers14.04.1) over (3.2.1-9~gpu14.04.1) ...
dpkg: ostrze&#380;enie: zast&#261;pienie vdpauinfo w wersji 1.0-1ubuntu1~gpu14.04.1 wcze&#347;niejsz&#261; wersj&#261; 0.1-1
Preparing to unpack .../vdpauinfo_0.1-1_amd64.deb ...
Unpacking vdpauinfo (0.1-1) over (1.0-1ubuntu1~gpu14.04.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-46-generic
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Konfigurowanie pakietu nvidia-settings (355.06-0ubuntu0~xedgers14.04.1) ...
Konfigurowanie pakietu bumblebee (3.2.1-5+xedgers14.04.1) ...


[COLOR=#ff0000][B]Configuration file '/etc/modprobe.d/bumblebee.conf' ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   Nale&#380;y wybra&#263; jedno z po&#347;ród wymienionych poni&#380;ej dzia&#322;a&#324;:
    Y lub I  : zainstalowanie wersji opiekuna pakietu (install)
    N lub O  : zachowanie bie&#380;&#261;cej wersji (do not change version)
      D      : pokazanie ró&#380;nic pomi&#281;dzy wersjami pliku (show differences betwen that files)
      Z      : uruchomienie pow&#322;oki w celu zbadania sytuacji (start smth to explore situation)
 Domy&#347;lnym dzia&#322;aniem jest zachowanie bie&#380;&#261;cej wersji. (default is do not change version)
*** bumblebee.conf (Y/I/N/O/D/Z) [domy&#347;lnie=N] ? [/B][/COLOR]
```

and one question to comments. If i good understand i need find that file, open by editor and write comment?

---

### Post by Bashing-om on 2015-08-23
jankupisz; Hummm ...

Not really sure what is going on that " Configuration file '/etc/modprobe.d/bumblebee.conf' ==> File on system created by you or by a script. " is invoked.
At what step in the procedure to remove the current driver do you encounter this situation ?

As BumbleBee will no longer be used by the system I expect we can remove the blacklist file . I do wonder what is calling it ? As I did look for a PPA for BumbleBee and did not see one .. I will look again just in the case that I did overlook the file. 

As to ;
> 
and one question to comments. If i good understand i need find that file, open by editor and write comment?

One does not 'NEED" to make any comments. Making a comment for any edits is just good practice to remind you of what/when/why at some later time you did make a change to the operating system.


[INDENT][INDENT][INDENT]best laid plans of mice and men
[INDENT][INDENT][INDENT][INDENT]and look what happens
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jankupisz on 2015-08-23
All you have in code -> last operation what i done is: **'sudo ppa-purge ppa:mamarley/nvidia' **and now i have that question :(

---

### Post by Bashing-om on 2015-08-23
jankupisz; Hey !

Let's try this :
```

sudo apt-get purge bumblebee bumblebee-nvidia primus

```
Once BumbleBee is removed we then remove the Nvidia PPAs .

[INDENT][INDENT][INDENT]maybe yes ?
[/INDENT][/INDENT][/INDENT]

---

### Post by jankupisz on 2015-08-23
but what i should choose from that option? install? or stay with old version?

---

### Post by Bashing-om on 2015-08-23
jankupisz; Wellll ..

> **jankupisz said:**
> but what i should choose from that option? install? or stay old version?

I do not think it really matters, but for this case 'Z' ; as we are going to remove Bumblebee anyway.

After Bumblebee is removed, might be good to see what remains in the referenced file:
```

cat /etc/modprobe.d/bumblebee.conf

```
with the expectation of a result "file not found" .

[INDENT][INDENT]think we can blame this one on me
[/INDENT][/INDENT]

---

### Post by jankupisz on 2015-08-23
so file not found ;)

and now i can't make last operation from first part of your tutorial because there is:
```
jasiek@jasiek-SATELLITE-L50-A:~$ [B]sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
[/B]mv:nie mo&#380;na wykona&#263; stat na &#8222;/etc/X11/xorg.conf&#8221;: Nie ma takiego pliku ani katalogu
```

it means, that it could not be done, because there is not that file

---

### Post by Bashing-om on 2015-08-23
jankupisz; Id OK;

No " /etc/X11/xorg.conf " file is acceptable. proceed on.
Edit the " /etc/apt/sources.list.d/ " files - OR we can remove them - and update the system.

[INDENT][INDENT]we proceed merrily on our way
[/INDENT][/INDENT]

---

### Post by jankupisz on 2015-08-23
I am happy man :) it installed 355.06 - i don't know it is ok?

and now NVIDIA X Server Settings loks like that: [http://scr.hu/1k0r/ez16h](http://scr.hu/1k0r/ez16h)
Thank you one more time! you are really awesome in ubuntu staff ;)

---

### Post by Bashing-om on 2015-08-23
jankupisz; Outstanding !

You do good work. I had faith in you all the time.
Pleased all worked out and you are up and running.
The 355 version is a bit on the cutting edge. But if it works for you, hey it works ! 

If this matter is now concluded to your satisfaction:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And I will wish
[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

### Post by jankupisz on 2015-08-23
i make it solved ;) but i have one more question - that 355.06 opensource is better than 346.82-updates from nvidia?

one more time thanks! Awesome job!

---

### Post by Bashing-om on 2015-08-23
jankupisz; Hey;

As you can see, 
> 
sudo ubuntu-drivers list
<snip>
nvidia-355

As you followed my directions, then ->
You now have the Nvidia proprietary version 355 installed. Which I do understand on most applications is better performing than that of the open source driver.
As you have installed the driver from our software repository, no longer do you have the worry of the driver breaking in updates !
The system ( package manager) will take care of it .
> 
is better than 346.82-updates from nvidia?

So, YES, is much better to install from our repository rather than from the less than ideal testing from Nvidia OEM. Once that driver hits our repository it is fully tested and found not only workable but tested to work ! Also keep in mind that Nvidia works very closely with our developers to provide that driver in our repository .

[INDENT][INDENT]wonderful things do happen
[/INDENT][/INDENT]

---

