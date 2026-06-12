---
title: "noob; how to check cpu speed and RAM capacity on ubuntu?"
date: 2019-03-03
forum: General Help
---

### Post by flyinghigh2 on 2019-03-03
noob; how to check cpu speed and RAM capacity on ubuntu?

hi I bought my computer second hand and am interested to know the cpu speed (think its 64)
and the amountof ram - is it easy to upgrade ram on a ubuntu laptop?

may thsanks:KS

---

### Post by again? on 2019-03-03
Install a sysinfo script called inxi.
```
sudo apt install inxi
```

If you don't want to install the recommended additional packages...
```
sudo apt --no-install-recommends install inxi
```

Some people who want to keep their system lean don't want the lm-sensors and hddtemp hardware monitoring packages
but also limits what inxi can show.
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] apt show inxi**
Package: inxi
Version: 2.3.56-1
Priority: extra
Section: universe/misc
Origin: Ubuntu
Maintainer: Unit 193 <unit193@ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 638 kB
Depends: gawk, pciutils, procps
[COLOR="#B22222"]**Recommends**: dmidecode, file, hddtemp, iproute2, kmod, lm-sensors, mesa-utils, net-tools, sudo, usbutils, x11-utils, x11-xserver-utils[/COLOR]
Homepage: http://smxi.org/docs/inxi.htm
Task: xubuntu-desktop, ubuntustudio-desktop, ubuntu-mate-core, ubuntu-mate-desktop
Supported: 3y
Download-Size: 143 kB
APT-Manual-Installed: yes
APT-Sources: http://ftp.iinet.net.au/pub/ubuntu bionic/universe amd64 Packages
Description: full featured system information script
 Inxi is a system information script that can display various things about
 your hardware and software to users in an IRC chatroom or support forum.
 It runs with the /exec command in most IRC clients.
```

To get a basic synopsis...
```
inxi -b
```

More info...
```
man inxi
inxi --help
```

---

### Post by cmcanulty on 2019-03-03
a nice graphical option is sysinfo

[ATTACH=CONFIG]282674[/ATTACH]

---

### Post by dragonfly41 on 2019-03-03
And another gui is found [here]("https://github.com/oguzhaninan/Stacer")

---

### Post by maglin2 on 2019-03-03
You could just type lshw into a terminal. The top 20 lines or so should give you the cpu speed and memory capacity (at least it does for me).

(For more specific output type lscpu and lsmem).

---

### Post by him610 on 2019-03-03
From the command line,
```
free -h && inxi -MSCD
```

---

### Post by flyinghigh2 on 2019-03-07
thanks 

I used 

```

free -h && inxi -MSCD

```

it says i have 1.7G mem is that RAM?

can this be upgraded?

```

free -h && inxi -MSCD
              total        used        free      shared  buff/cache   available
Mem:           1.7G        1.2G        137M         77M        409M        285M
Swap:          1.7G        903M        882M
System:    Host: rgmeager-Inspiron-M5030 Kernel: 4.4.0-142-generic x86_64 (64 bit)
           Desktop: Unity 7.4.5  Distro: Ubuntu 16.04 xenial
Machine:   System: Dell (portable) product: Inspiron M5030 v: A03
           Mobo: Dell model: Inspiron M5030 v: A03
           Bios: Dell v: A03 date: 09/10/2010
CPU:       Single core AMD V140 (-UP-) cache: 512 KB speed: 2300 MHz (max)
Drives:    HDD Total Size: 250.1GB (15.1% used)
           ID-1: /dev/sda model: ST9250315AS size: 250.1GB


```

Im used to upgrading ram in desktop machines but not laptop

the machine works well Ubuntu but I am looking to use autoCAD and this in Windows , 
runs slowly 

need a new machine really for AutoCAD

thanks for all your help

---

