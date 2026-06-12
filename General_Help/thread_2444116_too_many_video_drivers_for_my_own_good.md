---
title: "too many video drivers for my own good"
date: 2020-05-24
forum: General Help
---

### Post by kickass1955 on 2020-05-24
I wanted compiz to work in Ubuntu 18.04 so i found a compiz package to work.
i removed unity and i got rain effect to work and nothing else. upon reading in Ubuntu forums and tips on compiz
i loaded many video drivers for my system which now i regret. upon further reading i found a great site that got all my effects working
except rain effect. probable cause: vid. drivers. when i activate rain, screen goes black in background and i lose wallpaper.
al else works, burn, airplane, fire on close of window , wobbly windows, rotating cube....just no rain effect.
18.04 lts,  duo core, 16 gig of ram, hp laptop AMD processor . Using Ubuntu-Gnome Flashback, wallpaper comes back after 1 minute. put compiz --replace in startup app.
i guess i need to get rid of all video drivers and install original, but do not know how or maybe another way to fix this...HELP

---

### Post by Perfect Storm on 2020-05-24
Hello,

We need some information on which video card you have and how you installed these drivers.

regards,

---

### Post by kickass1955 on 2020-05-24
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Stoney [Radeon R2/R3/R4/R5 Graphics] (rev da)
the video drivers are ubuntu original...mesa drivers...xorg drivers...what command  to find out drivers
give me commands you need for info and i will get them for you... i also have a choice of gdm or lightdm
description: VGA compatible controller
       product: Stoney [Radeon R2/R3/R4/R5 Graphics]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: da
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=amdgpu latency=0

video drivers are:
joe@joe-HP-Laptop-15-db0xxx:~$ glxinfo | grep -i vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
    Vendor: X.Org (0x1002)
OpenGL vendor string: X.Org
       resources: irq:39 memory:e0000000-efffffff memory:f0000000-f07fffff ioport:4000(size=256) memory:f0c00000-f0c3ffff memory:c0000-dffff

---

### Post by deadflowr on 2020-05-25
> the video drivers are ubuntu original...mesa drivers...xorg drivers...what command to find out drivers
Where do you think you installed some other driver from?

FWIW, probably not a driver issue, as compiz plugins for various effects can break off and on.
Since there is less priority to keep them going or lack of developers to fix any issues.
I think some older animation effects that are still listed haven't properly functioned in years.
Or at least there have been some in recent pasts.

---

### Post by kickass1955 on 2020-05-25
i went by some compiz guides unfortunatley guides were old...ppa set for mesa... 
i did have rain effect working untill i started to add all kind of video drivers and should have done more research on settings in cssm

---

### Post by kickass1955 on 2020-05-25
i just want rain effect working and then i am done

---

### Post by deadflowr on 2020-05-25
Which ppa?

---

### Post by kickass1955 on 2020-05-25
ppa for latest mesa drivers
how do i find out....rusty at this...been 6 years

---

### Post by deadflowr on 2020-05-25
Not helpful.
We need the actual name of the ppa.
Could be either the padoka ppa or the oibaf ppa or any number of the literally thousands of ppas available.

---

### Post by kickass1955 on 2020-05-25
dd-apt-repository ppa:xorg-edgers/ppa

apt-repository ppa:oibaf/graphics-drivers

xserver-xorg-core

---

### Post by deadflowr on 2020-05-25
Both ppa describe what to do to revert back to the original packages:
[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers]("https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers")
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa?field.series_filter=bionic]("https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa?field.series_filter=bionic")

---

### Post by kickass1955 on 2020-05-25
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic main restricted
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates main restricted
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic universe
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates universe
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic multiverse
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates multiverse
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
/etc/apt/sources.list:deb [https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04/](https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04/) ./
/etc/apt/sources.list.d/xorg-edgers-ubuntu-ppa-bionic.list:deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) bionic main
/etc/apt/sources.list.d/webupd8team-ubuntu-y-ppa-manager-bionic.list:deb [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) bionic main
/etc/apt/sources.list.d/steam.list:deb [arch=amd64,i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam
/etc/apt/sources.list.d/oibaf-ubuntu-graphics-drivers-bionic.list:deb [http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu](http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu) bionic main
joe@joe-HP-Laptop-15-db0xxx:~$
Hope this is what you are asking for.

---

### Post by kickass1955 on 2020-05-25
thank you for all info...removing both ppa's now  will let you know results of the work

---

### Post by kickass1955 on 2020-05-25
ok removed and rebooted....got everything but rain effect...can any one help me to get it going?

---

