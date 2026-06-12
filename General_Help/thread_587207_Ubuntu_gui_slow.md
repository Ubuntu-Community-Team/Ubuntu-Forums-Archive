---
title: "Ubuntu gui slow"
date: 2007-10-22
forum: General Help
---

### Post by Immortalis on 2007-10-22
I'm trying Ubuntu as an alternative to windows XP, but I find the gui slow compared to. It feels like it's just constantly heavy when e.g. trying to switch between tabs in firefox, closing windows, moving them around or moving down a page in e.g. Cream. Especially the last one gives serious lag.

I'm running Gutsy on a znote 6224w - currenly using the restricted nvidia drives that I enabled in Ubuntu. I get 6k fps when running glxgears.

What can be wrong? Why is it going so slow? - no wonder linux users love the terminal ;)

---

### Post by 164747 on 2007-11-24
Yes I totally agree. I am experiancing the same thing. I dont know wether I should use the build in "enable restricted nvidia"-function or download a driver from the nvidia homepage. When I use the nvidia-homepage-solutiuon I get a higher value at glxgears but then Ubuntu wont let me enable compiz-fusion because it does not belive I have 3D-support. 

Not the differences below. However if I install with nvidia-homepage again I do not get the good score again. The 

install -> uninstall -> install

does not seem to give back the same thing again. 




With Ubuntu's Nvidia Restricted Driver
======================================

With CompizFusion:
21094 frames in 5.0 seconds = 4218.489 FPS
21313 frames in 5.0 seconds = 4262.449 FPS

Without CompizFusion:
28427 frames in 5.0 seconds = 5685.227 FPS
29873 frames in 5.0 seconds = 5974.542 FPS
29816 frames in 5.0 seconds = 5963.066 FPS


With Nvidia Driver -- from there HomePage
======================================
With CompizFusion:
??? Seems impossible to get ???

Without CompizFusion:
46250 frames in 5.0 seconds = 9249.963 FPS
!! Cannot reroduce !!

---

### Post by Zipster90 on 2007-11-24
What are the specs on the computer you're trying to run Ubuntu on? Ubuntu will work pretty snappily on most modern systems, but if it's an older system, you might want to try Xubuntu, which is supposed to be lighter on resources.

---

### Post by glaz_in_ua on 2007-11-30
> **Zipster90 said:**
> What are the specs on the computer you're trying to run Ubuntu on? Ubuntu will work pretty snappily on most modern systems, but if it's an older system, you might want to try Xubuntu, which is supposed to be lighter on resources.

I have the same problem. Firefox at WinXP works much faster than at Ubuntu. I've installed drivers from nVidia site. I have Athlon X2 4400+, GeForce8500GT and 2Gb memory. And I really think that for fast switching tabs in firefox that will be enough.

---

### Post by ryanlindstedt on 2007-12-05
I am having this same problem on a new computer 2.2ghz with 2gb of ram on 64bit anyone find a solution?

---

### Post by tomanytoremember on 2007-12-06
I am also having the same problem...

In Firefox I often use ctrl-mousewheel to zoom text in/out, in win xp its instantaneous, but in ubuntu it feels like it takes a solid second before it even begins to respond..

Somewhere else I read that disable pango would help, and it did, but not entirely...

I am using NVidia drivers from the restricted drivers app, running a fx5200, AMD 3200+, 1Gig of ram.

---

### Post by ryanlindstedt on 2007-12-08
I found out my problem actually. It was something to do with emerald. Any skin other that a "pixmap" and I think "legacy" will cause the problem on my system. It sucks, but I guess I'll just stick with the basic compiz  themes for now.

---

### Post by se7en.pt on 2008-04-25
I totally agree with this thread,
Im using Ubuntu 8.04, trying to "leave" Xp... but at this moment is impossible, unfortunatly, im running Core2Duo, its a good computer but the Ubuntu GUI is slow against Xp :(

---

### Post by sanemanmad on 2008-07-03
Hello All ~ I am also having same issue with GUI slowness.

I have used other distros in the past with the same video card and never had any problems.

os: 8.0 (hardy)
krnl:2.6.24-19-g
gdm: gnome 2.22.2
ram:1.2gb
AMD sempron 3000+
PCI:ATI Radeon 7000 ***
onboard AGP ATI Radeon Xpress 200 ***

*** I cannot for the live of me get dual monitors working either.... please help let me know what i need to post. I am quick in ubuntu and familiar with CLI. just hElp!

---

### Post by starcannon on 2008-07-03
My guess is that you are needing your video drivers installed correctly. For ATi perhaps start here [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) for Nvidia perhaps start here [http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia).  

Goodluck, and please don't assume that linux is broken when like any other OS it simply requires time to learn and get used to. Every OS needs drivers, and every OS requires you to learn how to install its drivers, in this regard, Linux of any flavor is no different.

```

starcannon-laptop
    description: Notebook
    product: HP Pavilion dv2500 Notebook PC
    vendor: Hewlett-Packard
    version: F.13
    serial: 2CE73816R4
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: U2E1
          size: 2001MHz
          capacity: 2001MHz
          width: 64 bits
          clock: 667MHz
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 2001MHz
          capacity: 2001MHz
          capabilities: vmx ht cpufreq
          configuration: id=1
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 2GiB
             configuration: driver=pcieport-driver
       *-display
                description: VGA compatible controller
                product: GeForce 8400M GS
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wmaster0
                version: 02
                serial: 00:1b:77:ce:a6:22
                width: 32 bits
                clock: 33MHz
           *-disk
                description: ATA Disk
                product: FUJITSU MHW2160B
                vendor: Fujitsu
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 891F
                serial: K10NT792SH2T
                size: 149GiB (160GB)

```

---

