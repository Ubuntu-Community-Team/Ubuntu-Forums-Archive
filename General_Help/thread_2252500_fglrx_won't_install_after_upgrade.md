---
title: "fglrx won't install after upgrade"
date: 2014-11-12
forum: General Help
---

### Post by Agnishom_Chattopadhyay on 2014-11-12
I just upgraded to 14.10 and now fglrx has been automatically removed. It does not want to install either.

```
chattopadhyay@chattopadhyayPC:~$ sudo apt-get install fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 fglrx : Depends: fglrx-core but it is not going to be installed
E: Unable to correct problems, you have held broken packages.



```

---

### Post by Bashing-om on 2014-11-12
Agnishom_Chattopadhyay; Hello

Maybe the card is out-of-support ?
What card is in use ?
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```

Supported card, then we might consider that a proprietary driver was broke in the upgrade process and requires (re-)installing.

Might try and purge FGLRX, install open source, try it - and then install a proprietary driver if the open source driver is not up to expectations.

[INDENT][INDENT][INDENT]just my thought
[/INDENT][/INDENT][/INDENT]

---

### Post by Agnishom_Chattopadhyay on 2014-11-12
I have a switchable ATI/Intel Graphics card.

```

chattopadhyay@chattopadhyayPC:~$ lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1669]
    Kernel driver in use: i915
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] [1002:6760]
    Subsystem: Hewlett-Packard Company Radeon HD 6470M [103c:1669]
    Kernel driver in use: radeon
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)


chattopadhyay@chattopadhyayPC:~$ sudo lshw -C display
[sudo] password for chattopadhyay: 
  *-display               
       description: VGA compatible controller
       product: Seymour [Radeon HD 6400M/7400M Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:47 memory:a0000000-afffffff memory:c6400000-c641ffff ioport:5000(size=256) memory:c6420000-c643ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:6050(size=8)

```

I believe I am already using the Open Source Driver(Mesa-utils says "direct-rendering is up and I'm using Galium on AMD") but it isn't as good as fglrx especially because of the higher working temperature of my laptop.

---

### Post by Bashing-om on 2014-11-12
Agnishom_Chattopadhyay; Well;

I have no experience with your graphics set, but I am aware of this :
[https://github.com/beidl/amd-indicator](https://github.com/beidl/amd-indicator) <- This indicator applet allows owners of laptops with AMD/Intel hybrid graphics capabilities to easily switch between the graphics cards without the need of running CCC or terminal commands.

I hope you find useful .

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by Agnishom_Chattopadhyay on 2014-11-13
Half way down the page(in the link you gave me), it says that I still need to install fglrx

---

### Post by Agnishom_Chattopadhyay on 2014-11-13
Any idea I can install fglrx anyway. My laptop seems to be overheating

---

### Post by Bashing-om on 2014-11-13
Agnishom_Chattopadhyay; Morning;

Yes, FGLRX needs to be installed.
Let's look and see what is is installed for FGLRX :
```

dpkg -l | grep fglrx

```

and we take the matter up from there.

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by Agnishom_Chattopadhyay on 2014-11-14
Hi;

That gives this

```

chattopadhyay@chattopadhyayPC:~$ dpkg -l | grep fglrx
rc  fglrx-updates                                        2:13.350.1-0ubuntu2                                 amd64        Video driver for the AMD graphics accelerators

```

---

### Post by Bashing-om on 2014-11-14
Agnishom_Chattopadhyay; Well, that ain't good .

This:
> 
rc  fglrx-updates 
 tells us the driver is (R)emoved, and (C)onfig files remain.

Let's try the easier approach in this situation and see what results:
```

sudo apt-get install fglrx-updates python-appindicator

```
Will require downloading the executable file(s), and adding the execute permissions to them.
This is but one possible solution of several.

[INDENT][INDENT]we can try, and see what works
[/INDENT][/INDENT]

---

### Post by Agnishom_Chattopadhyay on 2014-11-15
The same errror as in post 1 kicks in again when I key in your command

---

### Post by Bashing-om on 2014-11-15
Agnishom_Chattopadhyay; HoKay ;

Let's try this and see if we can clean things up and then install the FGLRX driver:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install dkms
sudo apt-get install fglrx fglrx-amdcccle
sudo amdconfig --initial

```


One way or another, I am sure we will have to get a driver installed.

[INDENT][INDENT]something is going to give
[/INDENT][/INDENT]

---

### Post by Agnishom_Chattopadhyay on 2014-11-16
Same thing :(
```

chattopadhyay@chattopadhyayPC:~$ sudo apt-get install fglrx fglrx-amdcccleReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 fglrx : Depends: fglrx-core but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by QIII on 2014-11-16
Hello!

fglrx-core is a package in Utopic.

Please go back up to post #11.  Follow Bashing-om's instructions, except for the last two lines.  

Instead of this

```

sudo apt-get install fglrx fglrx-amdcccle
sudo amdconfig --initial

```

I suggest -updates, including installation of fglrx-updates-core:

```

sudo apt-get install fglrx-updates-core fglrx-updates fglrx-amdcccle-updates
sudo amdconfig --initial

```

I don't have Utopic installed on an AMD/ATI machine, so I can't test this for you as I would like.

Give that a try and let us know how that goes.

Cheers.

---

### Post by Agnishom_Chattopadhyay on 2014-11-16
I removed wine and tried installing fglrx, it worked! :)

However, now when I want to get wine, it threatens it will remove fglrx :(

---

### Post by Scot_Bernard on 2015-03-17
```
sudo apt-get remove wine
sudo apt-get purge wine1.6
sudo apt-get install fglrx-updates
```

Worked for me.

> **Agnishom_Chattopadhyay said:**
> I removed wine and tried installing fglrx, it worked! :)

However, now when I want to get wine, it threatens it will remove fglrx :(

---

