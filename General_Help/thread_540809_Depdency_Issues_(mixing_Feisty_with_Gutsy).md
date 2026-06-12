---
title: "Depdency Issues (mixing Feisty with Gutsy)"
date: 2007-09-02
forum: General Help
---

### Post by fd9_ on 2007-09-02
I'm running Feisty, but I needed to grab a few packages from Gutsy in order for some things to work on my machine, as noted below:

- I grabbed the 2.6.22 binary kernel ( needed for mac80211 & wifi )
- I grabbed xserver-xorg-video-intel and libgl1-mesa-dri ( needed for Intel card, and the Gutsy version had fixed some problems I was having with the Feisty version )

...but now I'm starting to think that grabbing these packages from the Gutsy repositories was not such a good idea, because I'm starting to have dependency issues. For example, when I try to install build-essential, I get this:

( please note that my sources.list is clean, and there's nothing in there except for the normal Feisty repositories )

```

sudo apt-get update
sudo apt-get build-essential

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

```

And when I try aptitude instead of apt-get, it gets worse:

```

sudo aptitude update
sudo aptitude install build-essential

The following packages are BROKEN:
  libc6-dev 
The following NEW packages will be automatically installed:
  g++ g++-4.1 libstdc++6-4.1-dev linux-libc-dev 
The following packages have been kept back:
  linux-headers-2.6.20-16 linux-headers-2.6.20-16-generic 
  linux-image-2.6.20-16-generic 
The following NEW packages will be installed:
  build-essential g++ g++-4.1 libstdc++6-4.1-dev linux-libc-dev 
0 packages upgraded, 6 newly installed, 0 to remove and 3 not upgraded.
Need to get 7907kB of archives. After unpacking 33.0MB will be used.
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.5-0ubuntu14) but 2.6.1-1ubuntu1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-headers-2.6.22-10-generic
xbacklight

Downgrade the following packages:
libc6 [2.6.1-1ubuntu1 (now) -> 2.5-0ubuntu14 (feisty)]
libc6-i686 [2.6.1-1ubuntu1 (now) -> 2.5-0ubuntu14 (feisty)]
libgcc1 [1:4.2.1-4ubuntu1 (now) -> 1:4.1.2-0ubuntu4 (feisty)]
libgl1-mesa-dri [7.0.1-1ubuntu1 (now) -> 6.5.2-3ubuntu8 (feisty-updates)]
libgl1-mesa-glx [7.0.1-1ubuntu1 (now) -> 6.5.2-3ubuntu8 (feisty-updates)]
xserver-xorg-core [2:1.3.0.0.dfsg-12ubuntu2 (now) -> 2:1.2.0-3ubuntu8 (feisty)]
xserver-xorg-video-intel [2:2.1.1-0ubuntu2 (now) -> 2:1.9.94-1ubuntu3 (feisty,
feisty)]

Score is -1278

Accept this solution? [Y/n/q/?] 

```

So now I have two questions:

**1)** Why the heck does it want to downgrade these packages? What does xbacklight have to do with build-essentials? What do the Mesa drivers or the Intel drivers have to do with build-essentials?

**2)** Obviously I don't want to remove my 2.6.22 kernel, and I don't want to downgrade any of those packages! I want to keep the few Gusty packages that I have. I NEED those Gutsy packages. What do I do?

---

### Post by moore.bryan on 2007-09-02
> **fd9_ said:**
> 
**1)** Why the heck does it want to downgrade these packages? What does xbacklight have to do with build-essentials? What do the Mesa drivers or the Intel drivers have to do with build-essentials?
[I]it's not installing them because they're dependent on build-essentials, but because they aren't the version which should be on the system
[/I] > **fd9_ said:**
> 
**2)** Obviously I don't want to remove my 2.6.22 kernel, and I don't want to downgrade any of those packages! I want to keep the few Gusty packages that I have. I NEED those Gutsy packages. What do I do?
[I]for the gutsy kernel in feisty, there's a great post [here]("http://ubuntuforums.org/showthread.php?t=511974").  worked flawlessly for me.

now, for the rest of your issues.  one should **never** mix packages from one release with another.  now, having said that, sometimes you can get things to play nice.  do you have both gutsy and feisty repos in your /etc/apt/sources.list or are you downloading each package individually?
[/I]

---

### Post by frenchcr on 2007-09-02
**Oh..**  I upgraded to gutsy but i now have tons of repositories enabled...will i have conflicts between the feisty and gutsy repos... should i remove any of the following from my /etc/apt/sources.list

This is my sources.list

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty he fesirestricted main
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty restricted from 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates restricted main
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#AUTOMATIX REPOS START
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports restricted universe multiverse main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted multiverse universe main
#AUTOMATIX REPOS END

deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse

deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted main universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse

---

### Post by fd9_ on 2007-09-02
> **moore.bryan said:**
> [I]it's not installing them because they're dependent on build-essentials, but because they aren't the version which should be on the system
[/I] 
[I]for the gutsy kernel in feisty, there's a great post [here]("http://ubuntuforums.org/showthread.php?t=511974").  worked flawlessly for me.
[/I]

But no matter how I get the Gutsy kernel, isn't it still going to complain? All I did was download the binary using Synaptic.

> **moore.bryan said:**
> 
now, for the rest of your issues.  one should **never** mix packages from one release with another.  now, having said that, sometimes you can get things to play nice.  do you have both gutsy and feisty repos in your /etc/apt/sources.list or are you downloading each package individually?


No, I just have the usual Feisty repos in my sources.list. I still don't understand why I can't have the Intel/Mesa drivers from Gusty. It's the only two things I need, and I'm not planning on installing any other Gusty packages in the near future.

---

### Post by moore.bryan on 2007-09-02
> **frenchcr said:**
> **Oh..**  I upgraded to gutsy
[I]you're running gutsy?  i thought you said you were running feisty with some gutsy packages?  regardless, you sources.list should only ever have on or the other, **never both**.
[/I]> **frenchcr said:**
> but i now have tons of repositories enabled...will i have conflicts between the feisty and gutsy repos... should i remove any of the following from my /etc/apt/sources.list
*short answer, yes; long answer, maybe.  once again, you should only have one or the other.*
> **fd9_ said:**
> But no matter how I get the Gutsy kernel, isn't it still going to complain? All I did was download the binary using Synaptic.
[I]nope.  the link to the thread uses a script which only **temporarily ** changes the sources.list so you can upgrade the kernel and then returns everything back to "normal."
[/I]> **frenchcr said:**
> I still don't understand why I can't have the Intel/Mesa drivers from Gusty. It's the only two things I need, and I'm not planning on installing any other Gusty packages in the near future.
[I]you can have the latest "cutting- or bleeding-edge" programs, but people are advised to build them from source or find a compatible repo that ports them to your version for you.

if all you want/need are the intel/mesa drivers, you **could** go to [packages.ubuntu.com]("http://packages.ubuntu.com/"), search for the package you're looking for under the gutsy release, and check on all the packages listed as dependencies.  then, you'd need to upgrade each one of those, as well as your intel/mesa ones.  

just to let you know, it **could** take a while and cause a whole lot of frustration; however, in the long run, it could work and give you what you need.  the flip-side involves it never working and just being a wild-goose chase.

i went down that road with trying to install swiftweasel when it was only available from the debian unstable repos.  after two days of working on it, downloading/installing the packages manually, i finally got it going.  just took patience and perseverance.  if you want to go down that route, just let me know what i can do to help.

think of it this way, you've realized what takes a lot of people a lot of time: don't mix repos.  ;-)
[/I]

---

### Post by frenchcr on 2007-09-02
Thanks papa smurf. I was getting some strange things happening on boot up, but everything still worked fine once desktop was up.

I have removed all but gutsy repos from sources.list. Then cleaned out residual configs, orphans and ran a new update which installed new stuff and removed more obsloete packages.

Now Gutsy works better and loads quickly.

So the moral of the story, as you said, is that, at the moment, gutsy and feisty together is bad practice.

---

### Post by moore.bryan on 2007-09-02
[I]excellent... glad to hear you got it going.  i love and hate (at the same time) linux for the simple fact it's the best school of hard-knocks.  and as much as i hate it because it can be frustrating, i love it because it makes me work!  ;-)

happy ubuntu-ing.
[/I]

---

### Post by frenchcr on 2007-09-02
Thanks. Will i be able to upgrade to beta versions and final versions when they come long...wont have to reinstall or anything??

Your sentiments reflect my own. Im sort of new to linux but dont like easy street distros where everything just works out of the box...that way you dont learn anything. Its always a little worrying when something breaks but finding the fix is a learning process that i take pleasure from.

Problems i have still to fix with gutsy are:

Some keyboard characters are messed up...dont think its uk english.
Have to unclick and reclick Wired connection in Network settings every time i boot to get internet working.
No USB stick recognition.
No wireless for Intel(R) Wireless WiFi Link 4965AGN

May the learning resume :)

---

### Post by moore.bryan on 2007-09-02
[I]no problem.  since you've already installed the "most recent versions," ubuntu won't try to upgrade them until the package in the repos is more current than the ones you have.  no worries, there.

here, here.

for the usb issue, may i suggest ivman?  it's in the repos and i find it works exceptionally well for me with pnp.  as for wireless, you can see in my sig a link about wicd to manage wireless connections.

if your issue is the network card not even being seen, do me a favor and post the output of ```
lspci
sudo lshw -C network
iwconfig
```

no clue about the keyboard... leave it to you silly limeys.  ;-)
[/I]

---

### Post by frenchcr on 2007-09-02
oot@frenchcr03-lap:/home/frenchcr03# lspci
00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0407 (rev a1)
06:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05)
0a:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)


root@frenchcr03-lap:/home/frenchcr03# lspci
00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0407 (rev a1)
06:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05)
0a:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
root@frenchcr03-lap:/home/frenchcr03# sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:29:12:83
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:24:48:e6:f7
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full firmware=5787m-v3.23 ip=192.168.1.66 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
root@frenchcr03-lap:/home/frenchcr03# 


root@frenchcr03-lap:/home/frenchcr03# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid: 0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries: 0  Invalid misc:0   Missed beacon:0

root@frenchcr03-lap:/home/frenchcr03#

---

### Post by moore.bryan on 2007-09-02
*hmm... the wireless seems to be up and running.  try installing wicd (the link is in my sig) and use that to configure to which access point you want to connect.*

---

### Post by frenchcr on 2007-09-02
Thanks for ivman  found usb ->  /media/sdb1

Fixed keyboard chars, gutsy upgrade switched it to US English layout.

:-({|=

---

### Post by frenchcr on 2007-09-03
removed

---

### Post by rahimveron on 2007-09-03
> **frenchcr said:**
> wicd f***** bullshit...

papa surf is that a wind up website SOURCE FORGET ...jesus h christ

What Happened????

---

### Post by moore.bryan on 2007-09-03
> **frenchcr said:**
> wicd f***** bullshit...

papa surf is that a wind up website SOURCE FORGET ...jesus h christ

> **rahimveron said:**
> What Happened????

*huh?*

---

### Post by frenchcr on 2007-09-03
It just kept taking me to advertisement links, like the ones that retail search engines do.

have I misunderstood :confused:

Oh goodness your reaction lol maybe my mistake

---

### Post by imdano on 2007-09-03
There's a typo in the link to wicd's website in his signature.  It should be [http://wicd.sourceforge.net](http://wicd.sourceforge.net) not wicd.sourceforge**t**.net

---

### Post by moore.bryan on 2007-09-03
> **frenchcr said:**
> It just kept taking me to advertisement links, like the ones that retail search engines do.

have I misunderstood :confused:

Oh goodness your reaction lol maybe my mistake

> **imdano said:**
> There's a typo in the link to wicd's website in his signature.  It should be [http://wicd.sourceforge.net](http://wicd.sourceforge.net) not wicd.sourceforge**t**.net
[I]yikes!  that was it imdano... thanks a ton for catching that.  i've clicked it a bunch of times, but opendns kept correcting it for me.

sorry frenchcr for any misunderstanding!
[/I]

---

### Post by frenchcr on 2007-09-05
No probs papa smurf, thought you were too helpful to be a some kind of nasty advertising conman, but hey, you gotta watch out these days :lolflag:

PS. cheers for the new link !!

---

### Post by maestrobwh1 on 2007-12-30
You might want to read up on how to "pin" apt so that it favors packages in one repo over another:  Look at 
[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)[http://jaqque.sbih.org/kplug/apt-pinning.html]("http://jaqque.sbih.org/kplug/apt-pinning.html")

I found this more useful and even though it is for a specific computer, it does show how you can mix and match different repos.  It might be more useful, as it shows not only how to pin different sections of a distribution, but also how to pin different distributions.

[http://wiki.eeeuser.com/addingxandrosrepos](http://wiki.eeeuser.com/addingxandrosrepos)

The guide is self explanatory.  It basically tells apt where to choose a package from first.  Since Synaptic, Adept, Kpackage, Aptitude all are frontends for apt, it will also work with those items to help you not kill your system.

---

