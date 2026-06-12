---
title: "ubuntu mixes up soundcards randomly on boot"
date: 2007-05-14
forum: General Help
---

### Post by DjDarkman on 2007-05-14
The problem is that the kernel or alsa randomly mixes up my soundcards on boot sometimes, this is problematic, because on one boot my first soundcard is hw:0,0 an on the other it`s hw:1,0.

Is there a solution or workaround for this?it`s realy annoying, on every second or third boot, I have to set up my soundcards in every program that`s using them.

---

### Post by fragos on 2007-05-14
I had the same problem with two TV cards.  The solution is to write udev rules that create another mount point based not not on which one was mounted first but by the vendor and device codes.  I've included my notes for fixing the my problem.  You can follow the same proceedure.  Instead of /dev/video0 and 1 you may need to use /dev/audio1 and 2.  doing "ls /dev/audio*" will tell you which numbers go with "audio".  You'lll also want mount point names relating to audio and your two card models.

To get the device info for my cards, I used the following udevinfo commands:
Code:
udevinfo -a -p $(udevinfo -q path -n /dev/video0)
udevinfo -a -p $(udevinfo -q path -n /dev/video1)

fragos@Geo:~$ udevinfo -a -p $(udevinfo -q path -n /dev/video0) 

Udevinfo starts with the device specified by the devpath and then 
walks up the chain of parent devices. It prints for every device 
found, all possible attributes in the udev rules key format. 
A rule to match, can be composed by the attributes of the device 
and the attributes from one single parent device. 

  looking at device '/class/video4linux/video0': 
    KERNEL=="video0" 
    SUBSYSTEM=="video4linux" 
    DRIVER=="" 
    ATTR{card}=="10" 
    ATTR{name}=="BT878 video _Hauppauge _bt878__" 
    ATTR{dev}=="81:0" 

  looking at parent device '/devices/pci0000:00/0000:00:0a.0': 
    KERNELS=="0000:00:0a.0" 
    SUBSYSTEMS=="pci" 
    DRIVERS=="bttv" 
    ATTRS{msi_bus}=="" 
    ATTRS{broken_parity_status}=="0" 
    ATTRS{modalias}=="pci:v0000109Ed0000036Esv00000070sd000013EBbc04sc00i00" 
    ATTRS{local_cpus}=="ff" 
    ATTRS{irq}=="19" 
    ATTRS{class}=="0x040000" 
    ATTRS{subsystem_device}=="0x13eb" 
    ATTRS{subsystem_vendor}=="0x0070" 
    ATTRS{device}=="0x036e" 
    ATTRS{vendor}=="0x109e" 

  looking at parent device '/devices/pci0000:00': 
    KERNELS=="pci0000:00" 
    SUBSYSTEMS=="" 
    DRIVERS=="" 

fragos@Geo:~$ udevinfo -a -p $(udevinfo -q path -n /dev/video1) 

Udevinfo starts with the device specified by the devpath and then 
walks up the chain of parent devices. It prints for every device 
found, all possible attributes in the udev rules key format. 
A rule to match, can be composed by the attributes of the device 
and the attributes from one single parent device. 

  looking at device '/class/video4linux/video1': 
    KERNEL=="video1" 
    SUBSYSTEM=="video4linux" 
    DRIVER=="" 
    ATTR{name}=="ivtv0 encoder MPEG" 
    ATTR{dev}=="81:1" 

  looking at parent device '/devices/pci0000:00/0000:00:0b.0': 
    KERNELS=="0000:00:0b.0" 
    SUBSYSTEMS=="pci" 
    DRIVERS=="ivtv" 
    ATTRS{msi_bus}=="" 
    ATTRS{broken_parity_status}=="0" 
    ATTRS{modalias}=="pci:v00004444d00000016sv00000070sd00008801bc04sc00i00" 
    ATTRS{local_cpus}=="ff" 
    ATTRS{irq}=="20" 
    ATTRS{class}=="0x040000" 
    ATTRS{subsystem_device}=="0x8801" 
    ATTRS{subsystem_vendor}=="0x0070" 
    ATTRS{device}=="0x0016" 
    ATTRS{vendor}=="0x4444" 

  looking at parent device '/devices/pci0000:00': 
    KERNELS=="pci0000:00" 
    SUBSYSTEMS=="" 
    DRIVERS=="" 

fragos@Geo:~$ 

Since the Hauppauge includes multiple devices, video0, video24, and video32, I had to use the name of the proper device to get the proper mapping.

My final /etc/udev/rules.d/95-perso.rules file is:
Code:
KERNEL=="video*", SYSFS{vendor}=="0x4444", SYSFS{device}=="0x0016", SYSFS{name}=="ivtv0 encoder MPEG", SYMLINK+="video/pvr150"
KERNEL=="video*", SYSFS{vendor}=="0x109e", SYSFS{device}=="0x036e", SYMLINK+="video/bttv"
This results in the following symlinks:
Code:
/dev/video/pvr150
/dev/video/bttv

---

