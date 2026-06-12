---
title: "Backlight turns off on IBM T60P."
date: 2008-06-08
forum: General Help
---

### Post by andrias on 2008-06-08
Every now and then the backlight of my LCD is turning off. After CTRL-ALT-BACKSPACE, the light comes back on again.

A friend of mine said that dmesq could give valuable information, so here's the output of that command...

```
[ 1055.103151] compiz.real[5918]: segfault at 0003648b eip 08055a80 esp bfb48930 error 4
[ 1055.258372] [fglrx] interrupt source 10000000 successfully disabled!
[ 1055.258377] [fglrx] enable ID = 0x00000000
[ 1055.258379] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000008
[ 1058.696091] [fglrx] PCIe has already been initialized. Reinitializing ...
[ 1058.716029] [fglrx] Reserve Block - 0 offset =  0Xfffb000 length = 0X5000
[ 1058.716034] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[ 1058.716037] [fglrx] Reserve Block - 2 offset =  0Xffbb000 length = 0X40000
[ 1058.774451] [fglrx] interrupt source 10000000 successfully enabled
[ 1058.774457] [fglrx] enable ID = 0x00000008
[ 1058.774467] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[ 1069.040548] CPU0 attaching NULL sched-domain.
[ 1069.040553] CPU1 attaching NULL sched-domain.
[ 1069.066366] CPU0 attaching sched-domain:
[ 1069.066373]  domain 0: span 03
[ 1069.066376]   groups: 01 02
[ 1069.066380] CPU1 attaching sched-domain:
[ 1069.066381]  domain 0: span 03
[ 1069.066382]   groups: 02 01
```

Hardware information:

```
andrias@ANDRIAS:~$ sudo lshw -short
H/W path               Device      Class       Description
==========================================================
                                   system      20078LG
/0                                 bus         20078LG
/0/0                               memory      144KiB BIOS
/0/6                               processor   Intel(R) Core(TM)2 CPU         T7400  @ 2.16GHz
/0/6/a                             memory      64KiB L1 cache
/0/6/c                             memory      4MiB L2 cache
/0/6/1.1                           processor   Logical CPU
/0/6/1.2                           processor   Logical CPU
/0/b                               memory      64KiB L1 cache
/0/29                              memory      2GiB System Memory
/0/29/0                            memory      2GiB SODIMM Synchronous
/0/29/1                            memory      SODIMM Synchronous [empty]
/0/1                               processor   
/0/1/1.1                           processor   Logical CPU
/0/1/1.2                           processor   Logical CPU
/0/100                             bridge      Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hu
/0/100/1                           bridge      Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Por
/0/100/1/0                         display     M56GL [Mobility FireGL V5250]
/0/100/1b                          multimedia  82801G (ICH7 Family) High Definition Audio Controller
/0/100/1c                          bridge      82801G (ICH7 Family) PCI Express Port 1
/0/100/1c/0            eth0        network     82573L Gigabit Ethernet Controller
/0/100/1c.1                        bridge      82801G (ICH7 Family) PCI Express Port 2
/0/100/1c.1/0          wmaster0    network     PRO/Wireless 3945ABG Network Connection
/0/100/1c.2                        bridge      82801G (ICH7 Family) PCI Express Port 3
/0/100/1c.3                        bridge      82801G (ICH7 Family) PCI Express Port 4
/0/100/1d                          bus         82801G (ICH7 Family) USB UHCI Controller #1
/0/100/1d.1                        bus         82801G (ICH7 Family) USB UHCI Controller #2
/0/100/1d.2                        bus         82801G (ICH7 Family) USB UHCI Controller #3
/0/100/1d.3                        bus         82801G (ICH7 Family) USB UHCI Controller #4
/0/100/1d.7                        bus         82801G (ICH7 Family) USB2 EHCI Controller
/0/100/1e                          bridge      82801 Mobile PCI Bridge
/0/100/1e/0                        bridge      PCI1510 PC card Cardbus Controller
/0/100/1f                          bridge      82801GBM (ICH7-M) LPC Interface Bridge
/0/100/1f.1            scsi4       storage     82801G (ICH7 Family) IDE Controller
/0/100/1f.1/0.0.0      /dev/cdrom  disk        DVDRAM GSA-4083N
/0/100/1f.2            scsi0       storage     82801GBM/GHM (ICH7 Family) SATA AHCI Controller
/0/100/1f.2/0.0.0      /dev/sda    disk        100GB HITACHI HTS72201
/0/100/1f.2/0.0.0/1    /dev/sda1   volume      62GiB Windows NTFS volume
/0/100/1f.2/0.0.0/2    /dev/sda2   volume      26GiB Extended partition
/0/100/1f.2/0.0.0/2/5  /dev/sda5   volume      870MiB Linux swap / Solaris partition
/0/100/1f.2/0.0.0/2/6  /dev/sda6   volume      24GiB Linux filesystem partition
/0/100/1f.2/0.0.0/2/7  /dev/sda7   volume      1113MiB Linux swap / Solaris partition
/0/100/1f.2/0.0.0/3    /dev/sda3   volume      5049MiB Windows FAT volume
/0/100/1f.3                        bus         82801G (ICH7 Family) SMBus Controller
```

I'm quite new to Linux, so keep it simple.. :)

---

### Post by Rocket2DMn on 2008-06-08
Try checking the settings in gconf:
```
gconf-editor
```
Then go to /apps/gnome-power-manager and look at some of the settings.  Also look at the backlight subfolder, and possibly some others.
Some settings of interest:
gnome-power-manager: ac_dim_on_idle
backlight: idle_dim_ac, idle_dim_battery, brightness_ac, brightness_battery, enable, idle_dim_time
Time measurements are in seconds.

---

### Post by andrias on 2008-06-08
Settings seem OK. Dim is not active when running on AC and the backlight problem has happened while on AC.

I don't know if I've explained well enough, but I'll try again. The screen backlight completely turns off, resulting in the screen still showing the desktop, but without light.

Every time this has happened, there is the "compiz.real error" in the log..

---

### Post by Rocket2DMn on 2008-06-08
This sounds like either a hardware problem or a bug with compiz.  There are other reports on the forums and launchpad about people having screen and backlight problems with their Thinkpads, just google this and you will see:
```
site:launchpad.net compiz.real segfault thinkpad
```
You may want to file a bug report here - [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu) for the package compiz.  It is also possible that the problem is related to your video driver.  You can check the make/model of that by running
```
lspci | grep VGA
```
If you fill out a bug report, be sure to include your video card and the fact that you are using the restricted drivers (which would be for package linux-restrict-modules-some_kernel_version).

---

### Post by andrias on 2008-06-08
I think I've found a fix or a way to avoid the problem.

```
gconf-editor
```Go to "apps/gnome-power-manager/backlight/enable" and clear the checkbox.

---

### Post by andrias on 2008-06-14
The fix I previously posted has proven not to work after all. Any other bright ideas?

---

### Post by Rocket2DMn on 2008-06-14
I think that enable box should be checked.  Make sure idle_dim_ac is unchecked, and make sure brightness_ac is set to 100.  If you can't solve this problem with corret settings in gconf-editor or System->Preferences->Power Management, you may need to fill out a bug report at [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu) - explain your problem, the steps you have taken, and mark it for the compiz package.

---

### Post by kbnessa on 2008-06-22
This might not be related, although since the last time I updated my Kubuntu 8.04 installation on my T60p (a few days ago), I have had some weird issues with the backlight going off, and refusing to turn back on.

Although I do not use compiz, and in my case, restarting X does not usually fix it, I got to restart the computer (and in some cases, even that doesn't work).

Never had any issues like this before on this (2-3 year old) computer. Has there been any changes to ubuntu powermanagement recently that can possibly relate to this?

---

