---
title: "camera not detecting"
date: 2023-10-21
forum: General Help
---

### Post by umutr42 on 2023-10-21
Hello, I think my laptop cannot detect my camera. There are no video0/ and video/ files, can you help me? there is some outs

*-usb:2 UNCLAIMED
                   description: Generic USB device
                   product: ELAN:Fingerprint
                   vendor: ELAN
                   physical id: 8
                   bus info: usb@3:8
                   version: 1.65
                   capabilities: usb-2.00
                   configuration: maxpower=100mA speed=12Mbit/s


umutr42@umutr42-Aspire-A715-51G:/$ v4l2-ctl --list-devices
Cannot open device /dev/video0, exiting.

---

### Post by readableauthor on 2023-10-21
Post output of this command:
```

lspci -nn && lsusb

```

---

### Post by umutr42 on 2023-10-21
@[**[COLOR=#000000]readableauthor[/COLOR]**]("https://ubuntuforums.org/member.php?u=2169893") 

0000:00:00.0 Host bridge [0600]: Intel Corporation Device [8086:4621] (rev 02)
0000:00:02.0 VGA compatible controller [0300]: Intel Corporation Alder Lake-P Integrated Graphics Controller [8086:4626] (rev 0c)
0000:00:04.0 Signal processing controller [1180]: Intel Corporation Alder Lake Innovation Platform Framework Processor Participant [8086:461d] (rev 02)
0000:00:06.0 PCI bridge [0604]: Intel Corporation 12th Gen Core Processor PCI Express x4 Controller #0 [8086:464d] (rev 02)
0000:00:07.0 PCI bridge [0604]: Intel Corporation Alder Lake-P Thunderbolt 4 PCI Express Root Port #0 [8086:466e] (rev 02)
0000:00:08.0 System peripheral [0880]: Intel Corporation 12th Gen Core Processor Gaussian & Neural Accelerator [8086:464f] (rev 02)
0000:00:0a.0 Signal processing controller [1180]: Intel Corporation Platform Monitoring Technology [8086:467d] (rev 01)
0000:00:0d.0 USB controller [0c03]: Intel Corporation Alder Lake-P Thunderbolt 4 USB Controller [8086:461e] (rev 02)
0000:00:0d.2 USB controller [0c03]: Intel Corporation Alder Lake-P Thunderbolt 4 NHI #0 [8086:463e] (rev 02)
0000:00:0e.0 RAID bus controller [0104]: Intel Corporation Volume Management Device NVMe RAID Controller [8086:467f]
0000:00:14.0 USB controller [0c03]: Intel Corporation Alder Lake PCH USB 3.2 xHCI Host Controller [8086:51ed] (rev 01)
0000:00:14.2 RAM memory [0500]: Intel Corporation Alder Lake PCH Shared SRAM [8086:51ef] (rev 01)
0000:00:15.0 Serial bus controller [0c80]: Intel Corporation Alder Lake PCH Serial IO I2C Controller #0 [8086:51e8] (rev 01)
0000:00:15.1 Serial bus controller [0c80]: Intel Corporation Alder Lake PCH Serial IO I2C Controller #1 [8086:51e9] (rev 01)
0000:00:16.0 Communication controller [0780]: Intel Corporation Alder Lake PCH HECI Controller [8086:51e0] (rev 01)
0000:00:1c.0 PCI bridge [0604]: Intel Corporation Device [8086:51bb] (rev 01)
0000:00:1c.6 PCI bridge [0604]: Intel Corporation Device [8086:51be] (rev 01)
0000:00:1f.0 ISA bridge [0601]: Intel Corporation Alder Lake PCH eSPI Controller [8086:5182] (rev 01)
0000:00:1f.3 Multimedia audio controller [0401]: Intel Corporation Alder Lake PCH-P High Definition Audio Controller [8086:51c8] (rev 01)
0000:00:1f.4 SMBus [0c05]: Intel Corporation Alder Lake PCH-P SMBus Host Controller [8086:51a3] (rev 01)
0000:00:1f.5 Serial bus controller [0c80]: Intel Corporation Alder Lake-P PCH SPI Controller [8086:51a4] (rev 01)
0000:01:00.0 3D controller [0302]: NVIDIA Corporation GA107M [GeForce RTX 3050 Mobile] [10de:25a2] (rev a1)
0000:3d:00.0 Network controller [0280]: MEDIATEK Corp. MT7921 802.11ax PCI Express Wireless Network Adapter [14c3:7961]
0000:3e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
10000:e0:06.0 System peripheral [0880]: Intel Corporation Device [8086:09ab]
10000:e0:06.2 PCI bridge [0604]: Intel Corporation 12th Gen Core Processor PCI Express x4 Controller #2 [8086:463d] (rev 02)
10000:e1:00.0 Non-Volatile memory controller [0108]: Micron Technology Inc Device [1344:5411] (rev 01)
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 04f3:0c4f Elan Microelectronics Corp. ELAN:Fingerprint
Bus 003 Device 003: ID 0408:4033 Quanta Computer, Inc. ACER HD User Facing
Bus 003 Device 005: ID 04ca:3802 Lite-On Technology Corp. Wireless_Device
Bus 003 Device 002: ID 30fa:1040 INSTANT SMX-R47
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by readableauthor on 2023-10-21
Your webcam is not well supported by Linux as of now. But there's a way to make it work:
[https://ubuntuforums.org/showthread.php?t=2477627&p=14147432#post14147432](https://ubuntuforums.org/showthread.php?t=2477627&p=14147432#post14147432)
I assume you'd have to downgrade to Linux 5.15 if you're running 6.2

---

### Post by MAFoElffen on 2023-10-21
Well maybe not. 

The custom module was written for 5.15.0 but...That bug report has instructions for grabbing the relevant  current kernel version source (and which line in that module source to modify) to compile the module for the kernel you are running... That still is no guaranty that it will work for 6.2, but there is hope. 

But you would have to understand that "that " is a lot of work, for something that you would have to redo every time the Linux kernel updated (recompile and insert the newly compiled module). 

The reviews on that built-in internal webcam were that it was very low quality. It might be easier and better in the long run to look into an external USB WecCam that is better quality and better supported in Linux. I have had no problem with Logitech WebCams, and they do not cost much at all..

---

### Post by umutr42 on 2023-10-26
> **MAFoElffen said:**
> Well maybe not. 

The custom module was written for 5.15.0 but...That bug report has instructions for grabbing the relevant  current kernel version source (and which line in that module source to modify) to compile the module for the kernel you are running... That still is no guaranty that it will work for 6.2, but there is hope. 

But you would have to understand that "that " is a lot of work, for something that you would have to redo every time the Linux kernel updated (recompile and insert the newly compiled module). 

The reviews on that built-in internal webcam were that it was very low quality. It might be easier and better in the long run to look into an external USB WecCam that is better quality and better supported in Linux. I have had no problem with Logitech WebCams, and they do not cost much at all..

So how can I do this? I am also thinking of buying it for a USB web camera, but I would like it if the laptop had its own camera, of course, if there is any hope.; ))

---

### Post by readableauthor on 2023-10-26
Try running the instructions I linked

---

### Post by umutr42 on 2023-10-30
Hello. I tried it but I encountered some problems, for example it said that sources.list.save was invalid, then I deleted it and also the source-list.d file was empty. How do I update them again? ( i am stupit i know ./)

apt-get source linux-modules-extra-$(uname -r)
 in the command:

E: Source package for package linux-hwe-6.2 not found
 I'm getting an error. I'll put the detailed information below. ;)

```

umutr42@umutr42-Aspire-A715-51G:/etc$ cd apt
umutr42@umutr42-Aspire-A715-51G:/etc/apt$ ls
apt.conf.d   keyrings       sources.list    trusted.gpg
auth.conf.d  preferences.d  sources.list.d  trusted.gpg.d
umutr42@umutr42-Aspire-A715-51G:/etc/apt$ cd sources.list.d/
umutr42@umutr42-Aspire-A715-51G:/etc/apt/sources.list.d$ ls
umutr42@umutr42-Aspire-A715-51G:/etc/apt/sources.list.d$ 


```
```


umutr42@umutr42-Aspire-A715-51G:~$ sudo apt update
Hit:1 http://tr.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://tr.archive.ubuntu.com/ubuntu jammy-updates InRelease  
Hit:3 http://tr.archive.ubuntu.com/ubuntu jammy-backports InRelease
Hit:4 http://archive.ubuntu.com/ubuntu jammy-proposed InRelease    
Hit:5 http://security.ubuntu.com/ubuntu jammy-security InRelease   
Hit:6 http://in.archive.ubuntu.com/ubuntu lunar InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.



umutr42@umutr42-Aspire-A715-51G:~$ sudo apt install build-essential -y 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
build-essential is already the newest version (12.9ubuntu3).
The following package was automatically installed and is no longer required:
  nvidia-firmware-535-535.86.05
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
  


umutr42@umutr42-Aspire-A715-51G:~$ apt-get source linux-modules-extra-$(uname -r)
Reading package lists... Done
Picking 'linux-hwe-6.2' as source package instead of 'linux-modules-extra-6.2.0-35-generic'
E: Unable to find a source package for linux-hwe-6.2
umutr42@umutr42-Aspire-A715-51G:~$ 



```


And
```

umutr42@umutr42-Aspire-A715-51G:/etc/apt$ cat sources.list
# deb cdrom:[Ubuntu 22.04.3 LTS _Jammy Jellyfish_ - Release amd64 (20230807.2)]/ jammy main restricted
deb-src http://in.archive.ubuntu.com/ubuntu lunar main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://tr.archive.ubuntu.com/ubuntu/ jammy main restricted
deb http://archive.ubuntu.com/ubuntu/ jammy-proposed main
## Major bug fix updates produced after the final release of the
## distribution.
deb http://tr.archive.ubuntu.com/ubuntu/ jammy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://tr.archive.ubuntu.com/ubuntu/ jammy universe
# deb-src http://tr.archive.ubuntu.com/ubuntu/ jammy universe
deb http://tr.archive.ubuntu.com/ubuntu/ jammy-updates universe
# deb-src http://tr.archive.ubuntu.com/ubuntu/ jammy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://tr.archive.ubuntu.com/ubuntu/ jammy multiverse
# deb-src http://tr.archive.ubuntu.com/ubuntu/ jammy multiverse
deb http://tr.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
# deb-src http://tr.archive.ubuntu.com/ubuntu/ jammy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://tr.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu jammy-security main restricted
deb http://security.ubuntu.com/ubuntu jammy-security universe
# deb-src http://security.ubuntu.com/ubuntu jammy-security universe
deb http://security.ubuntu.com/ubuntu jammy-security multiverse
# deb-src http://security.ubuntu.com/ubuntu jammy-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
```

@[**[COLOR=#000000]andrianovig[/COLOR]**]("https://ubuntuforums.org/member.php?u=2179920")**[COLOR=#000000]or @[/COLOR]**[**[COLOR=#000000]readableauthor[/COLOR]**]("https://ubuntuforums.org/member.php?u=2169893")

---

