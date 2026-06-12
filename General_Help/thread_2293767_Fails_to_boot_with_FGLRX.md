---
title: "Fails to boot with FGLRX"
date: 2015-09-07
forum: General Help
---

### Post by jtdemille on 2015-09-07
I'm planning on moving over to Linux, but if I run a Source engine game in Steam, it throws an error about the graphics driver. So I installed FGLRX, it failed to boot. I went into recovery mode and removed it. Tried AMD Catalyst drivers, same thing. Gets worse with Minecraft, though. If I do certain things such as play on a server that uses BungeeCord, X can sometimes lock up. Can anybody help me out with this?

---

### Post by Bashing-om on 2015-09-07
jtdemille; Hi Welcome to the forum.

Sure we can find out what is going on here.
The factors are how much ram you have on the system, how the system handles swap, and most importantly is what graphics card you have installed.
Post back - Between code tags - the outputs of terminal commands :
```

free -m
lspci -vnn | grep VGA -A 12
sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]we see then
[INDENT][INDENT][INDENT]what story gets told
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by QIII on 2015-09-07
Hello!

I'd just like to point out that fglrx and Catalyst are the same driver.  More properly, perhaps:  "Catalyst" is the fglrx driver with the accompanying Catalyst Control Center.  Further, the fglrx driver in the Ubuntu repo is the exact same driver as AMD had on their website at the time of the particular Ubuntu release.  This happens every 4th and 10th month as Ubuntu is released.  AMD makes their driver available to Canonical at release time so that it can be included in the repo.  This is a somewhat unique relationship between AMD and Canonical.

However, fglrx is not supported on all AMD GPUs in Linux.  AMD has withdrawn Linux driver support for many GPUs.  If you have one of those adapters, fglrx may simply not work.  If your adapter is supported, one of the most common reasons that it does not work is that the driver was not initialized before rebooting.  That is a very easy thing to do and may entirely solve the issue.

So please provide the information Bashing-om has requested so we know where to go.

---

### Post by jtdemille on 2015-09-07
> **Bashing-om said:**
> jtdemille; Hi Welcome to the forum.

Sure we can find out what is going on here.
The factors are how much ram you have on the system, how the system handles swap, and most importantly is what graphics card you have installed.
Post back - Between code tags - the outputs of terminal commands :
```

free -m
lspci -vnn | grep VGA -A 12
sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)[INDENT][INDENT]we see then[INDENT][INDENT][INDENT]what story gets told
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

free -m:
```

             total       used       free     shared    buffers     cached
Mem:         15909      12781       3127        139       3662       6375
-/+ buffers/cache:       2744      13165
Swap:         5640          0       5640

```
lspci -vnn | grep VGA -A 12:
```

00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06) (prog-if 00 [VGA controller])
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:d000]
    Flags: bus master, fast devsel, latency 0, IRQ 36
    Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: i915


00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
    Subsystem: Intel Corporation Device [8086:2010]
    Flags: bus master, fast devsel, latency 0, IRQ 37
    Memory at f7e34000 (64-bit, non-prefetchable) [size=16K]
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde PRO [Radeon HD 7750 / R7 250E] [1002:683f] (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:2794]
    Flags: bus master, fast devsel, latency 0, IRQ 38
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f7d00000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at e000 [size=256]
    Expansion ROM at f7d40000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon


01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series] [1002:aab0]
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:aab0]
    Flags: bus master, fast devsel, latency 0, IRQ 35

```

sudo lshw -C display:
```

 *-display               
       description: VGA compatible controller
       product: Cape Verde PRO [Radeon HD 7750 / R7 250E]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:38 memory:e0000000-efffffff memory:f7d00000-f7d3ffff ioport:e000(size=256) memory:f7d40000-f7d5ffff
  *-display
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: driver=i915 latency=0
       resources: irq:36 memory:f7800000-f7bfffff memory:d0000000-dfffffff ioport:f000(size=64)

```
Do note that I have used FGLRX on previous installs and had no issues, with the same computer. Maybe it's because of the addition of the Intel CPU, or having a 2nd monitor? Also, I intentionally had less than 16GB of swap.

---

### Post by Bashing-om on 2015-09-07
jtdemille' Yeah !

Decent little box there. ram and swap are not an issue - 16 Gigs of ram, /swap will rarely if ever be used - . Pretty good graphics card that will support FGLRX.

So prior to installing the proprietary driver, what is presently on the system ?
```

dpkg -l | grep fglrx

```
that we should remove.

[INDENT][INDENT]look'n good
[INDENT][INDENT][INDENT]for the home team
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jtdemille on 2015-09-07
> **Bashing-om said:**
> jtdemille' Yeah !

Decent little box there. ram and swap are not an issue - 16 Gigs of ram, /swap will rarely if ever be used - . Pretty good graphics card that will support FGLRX.

So prior to installing the proprietary driver, what is presently on the system ?
```

dpkg -l | grep fglrx

```
that we should remove.[INDENT][INDENT]look'n good[INDENT][INDENT][INDENT]for the home team
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

```

rc  fglrx-updates                               2:15.200-0ubuntu4.2                     amd64        Video driver for the AMD graphics accelerators
rc  fglrx-updates-core                          2:15.200-0ubuntu4.2                     amd64        Minimal video driver for the AMD graphics accelerators

```
Wait, how the heck did those get there? Let me guess, "apt-get purge fglrx-updates fglrx-updates-core"

---

### Post by Bashing-om on 2015-09-07
jtdemille; HoKay !

Let's remove the "rc" Files, and install all anew.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

In 14.04+ we have new tools to deal with proprietary drivers.
What results:
```

sudo ubuntu-drivers devices
sudo ubuntu-drivers list
sudo ubuntu-drivers autoinstall

```
to install the standard available proprietary video driver; This will install the latest proprietary video driver. If the proprietary video driver is already installed then this command will only read the package lists and rebuild the dependency tree. If that happens then you know you have the proprietary driver installed.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by jtdemille on 2015-09-07
> **Bashing-om said:**
> jtdemille; HoKay !

Let's remove the "rc" Files, and install all anew.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

In 14.04+ we have new tools to deal with proprietary drivers.
What results:
```

sudo ubuntu-drivers devices
sudo ubuntu-drivers list
sudo ubuntu-drivers autoinstall

```
to install the standard available proprietary video driver; This will install the latest proprietary video driver. If the proprietary video driver is already installed then this command will only read the package lists and rebuild the dependency tree. If that happens then you know you have the proprietary driver installed.
[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]

```

firefaced@SUPERPC-ubuntu:~$ sudo ubuntu-drivers devices
== cpu-microcode.py ==
driver   : intel-microcode - distro non-free


== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
model    : Cape Verde PRO [Radeon HD 7750 / R7 250E]
modalias : pci:v00001002d0000683Fsv00001462sd00002794bc03sc00i00
vendor   : Advanced Micro Devices, Inc. [AMD/ATI]
driver   : fglrx-updates - distro non-free
driver   : xserver-xorg-video-ati - distro free builtin recommended
driver   : fglrx - distro non-free


firefaced@SUPERPC-ubuntu:~$ sudo ubuntu-drivers list
fglrx
fglrx-updates
intel-microcode
firefaced@SUPERPC-ubuntu:~$ sudo ubuntu-drivers autoinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms lib32gcc1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  iucode-tool
The following NEW packages will be installed:
  intel-microcode iucode-tool
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 466 kB of archives.
After this operation, 691 kB of additional disk space will be used.
Get:1 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ vivid/restricted iucode-tool amd64 1.1.1-1 [31.0 kB]
Get:2 http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ vivid/restricted intel-microcode amd64 3.20150121.1 [435 kB]
Fetched 466 kB in 0s (758 kB/s)         
Selecting previously unselected package iucode-tool.
(Reading database ... 212243 files and directories currently installed.)
Preparing to unpack .../iucode-tool_1.1.1-1_amd64.deb ...
Unpacking iucode-tool (1.1.1-1) ...
Selecting previously unselected package intel-microcode.
Preparing to unpack .../intel-microcode_3.20150121.1_amd64.deb ...
Unpacking intel-microcode (3.20150121.1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Setting up iucode-tool (1.1.1-1) ...
Setting up intel-microcode (3.20150121.1) ...
update-initramfs: deferring update (trigger activated)
intel-microcode: microcode will be updated at next boot
Processing triggers for initramfs-tools (0.103ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-26-generic

```
I don't know what this means, but it looks like it installed the Intel drivers. :/

---

### Post by Bashing-om on 2015-09-07
jtdemille; Hymmm ...

Not had this result before !
Pardon me while I scratch my head and ponder this: - not to hold you up -

The driver is found:
> 
driver   : fglrx-updates - distro non-free

Yeah, only intel-microcode(s) were installed. Presently I can not fathom why "autoinstall" would fail to install the graphic's driver.

Lemme think this over, maybe resort back to manually installing (apt-get install what-we-want) .

[INDENT][INDENT]sometimes I wonder
[/INDENT][/INDENT]

---

### Post by jtdemille on 2015-09-07
Okay.

---

### Post by Bashing-om on 2015-09-07
jtdemille; OK;

Long standing bug:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491)
That "should" now be fixed - still unknown why "autoinstall" fails -

Let's see what results:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install linux-headers-generic
apt-get install fglrx-updates
sudo amdconfig --initial

```

Maybe yes ?
[INDENT][INDENT]still could be not so yes
[/INDENT][/INDENT]

---

### Post by jtdemille on 2015-09-07
> **Bashing-om said:**
> jtdemille; OK;

Long standing bug:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491)
That "should" now be fixed - still unknown why "autoinstall" fails -

Let's see what results:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install linux-headers-generic
apt-get install fglrx-updates
sudo amdconfig --initial

```

Maybe yes ?[INDENT][INDENT]still could be not so yes
[/INDENT]
[/INDENT]

I'm currently doing stuff, what would dist-upgrade do?

---

### Post by Bashing-om on 2015-09-07
jtdemille; Hey.

"dist-upgrade" is to install the latest kernel in that install, it has nothing to do with upgrading to a new release;
As "apt-get update" will not install anything 'new' .

[INDENT][INDENT]fingers are crossed
[/INDENT][/INDENT]

---

### Post by jtdemille on 2015-09-07
It boots. Let's see if games work

---

### Post by jtdemille on 2015-09-07
All right, now Portal 2 opens, but not in X.
EDIT: This is out of the scope of this thread, so I'm going to close the thread since I got it to boot with FGLRX.

---

### Post by jtdemille on 2015-09-07
Can a moderator close this thread?

---

### Post by Bashing-om on 2015-09-07
jtdemille; Good deal;

I do not game so can offer no additional advise, so yeah close this thread IF you are satisfied.
Only you can determine that status and " mark this thread solved". At the top of the post -> thread tools .
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]Good deeds done
[INDENT][INDENT][INDENT]dirt cheap
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jtdemille on 2015-09-07
Yep, marked as solved.

---

