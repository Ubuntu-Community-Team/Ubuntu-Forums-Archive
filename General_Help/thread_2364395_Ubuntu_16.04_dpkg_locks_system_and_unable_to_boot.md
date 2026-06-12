---
title: "Ubuntu 16.04 dpkg locks system and unable to boot"
date: 2017-06-22
forum: General Help
---

### Post by Drenriza on 2017-06-22
I am trying to update and upgrade a pi3 running
> Linux rproxy01 4.4.0-1009-raspi2 #10-Ubuntu SMP Tue Apr 19 19:51:04 UTC 2016 armv7l armv7l armv7l GNU/Linux
downloaded from [https://wiki.ubuntu.com/ARM/RaspberryPi](https://wiki.ubuntu.com/ARM/RaspberryPi)
Raspberry Pi 3: ubuntu-16.04-preinstalled-server-armhf+raspi3.img.xz (4G image, 216M compressed)

But i keep getting an error saying that dpkg ran into an error while processing an archive,
to get around this i tried the following
```
apt-get clean
apt-get update && apt-get upgrade -y
```
> 
Hit:1 [http://ppa.launchpad.net/ubuntu-raspi2/ppa-rpi3/ubuntu](http://ppa.launchpad.net/ubuntu-raspi2/ppa-rpi3/ubuntu) xenial InRelease
Hit:2 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial InRelease
Hit:3 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates InRelease
Hit:4 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-backports InRelease
Hit:5 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security InRelease
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-headers-raspi2 linux-image-raspi2 linux-raspi2 vim vim-common vim-runtime vim-tiny
The following packages will be upgraded:
  linux-firmware
1 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
137 not fully installed or removed.
Need to get 37.9 MB of archives.
After this operation, 39.2 MB of additional disk space will be used.
Get:1 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main armhf linux-firmware all 1.157.11 [37.9 MB]
Fetched 37.9 MB in 13s (2,739 kB/s)                                                                                       
(Reading database ... 50385 files and directories currently installed.)
Preparing to unpack .../linux-firmware_1.157.11_all.deb ...
Unpacking linux-firmware (1.157.11) over (1.157) ...
[B]dpkg: error processing archive /var/cache/apt/archives/linux-firmware_1.157.11_all.deb (--unpack):
 trying to overwrite '/lib/firmware/brcm/brcmfmac43430-sdio.bin', which is also in package linux-firmware-raspi2 1.20161020-0ubuntu1~0.2~rpi3
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-firmware_1.157.11_all.deb[/B]
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
dpkg -i --force-overwrite /var/cache/apt/archives/linux-firmware_1.157.11_all.deb
```
> (Reading database ... 50385 files and directories currently installed.)
Preparing to unpack .../linux-firmware_1.157.11_all.deb ...
Unpacking linux-firmware (1.157.11) over (1.157) ...
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/lib/firmware/brcm/brcmfmac43430-sdio.bin', which is also in package linux-firmware-raspi2 1.20161020-0ubuntu1~0.2~rpi3
Setting up linux-firmware (1.157.11) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-1009-raspi2
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
flash-kernel: deferring update (trigger activated)

```
apt-get -f install
```

Everything than looked like it got installed and apt-get showed that the packages got installed with 7 packages held back
> root@rproxy01:~# apt-get update
Hit:1 [http://ppa.launchpad.net/ubuntu-raspi2/ppa-rpi3/ubuntu](http://ppa.launchpad.net/ubuntu-raspi2/ppa-rpi3/ubuntu) xenial InRelease
Hit:2 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial InRelease
Hit:3 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates InRelease
Hit:4 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-backports InRelease
Get:5 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security InRelease [102 kB]
Fetched 102 kB in 2s (40.2 kB/s)                             
Reading package lists... Done
root@rproxy01:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-headers-raspi2 linux-image-raspi2 linux-raspi2 vim vim-common vim-runtime vim-tiny
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

After a reboot i get the following error 
> 
Ethernet connection... unable to connect.
environment variable: pxeuuid
environment variable: bootfile
saving file: pxelinux.cfg/01-b8-27-3b...

repeated over and over for different pxelinux.cfg files, and the system is no longer able to boot.
This error also occures if i only run apt-get update and upgrade without forcefully overwriting files.

Anyone who know what is going on with my dpkg?
Any help is highly appreciated.

Thanks in advance

---

### Post by Drenriza on 2017-06-24
Anyone?

---

### Post by ian-weisser on 2017-06-24
Well, the answer seems right there in the error message:

> **Drenriza said:**
> ```
dpkg: error processing archive /var/cache/apt/archives/linux-firmware_1.157.11_all.deb (--unpack):
trying to overwrite '/lib/firmware/brcm/brcmfmac43430-sdio.bin', which is also in package linux-firmware-raspi2 1.20161020-0ubuntu1~0.2~rpi3
```

Those two packages are *incompatible*. You cannot have both installed at the same time.

You can try uninstalling linux-firmware,
Or you can try force-installing linux-firmware...but beware - it might brick your pi.

You should let the ppa owner know that their package breaks linux-firmware. They may not have intended that.Or they may have a mistake in their deb control file.

---

