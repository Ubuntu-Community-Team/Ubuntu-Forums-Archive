---
title: "Ubuntu on Flash Drive"
date: 2017-09-06
forum: General Help
---

### Post by daniell59 on 2017-09-06
I downloaded Ubuntu 16.04.3 onto a flash drive using Startup Disk Creator. I then tried to boot into it with no success. Please see image.

---

### Post by sudodus on 2017-09-06
This looks like an old bug for the Startup Disk Creator running in Ubuntu versions older than 16.04 LTS.

Please try with mkusb according to the following links,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkUSB-quick-start-manual-12](https://help.ubuntu.com/community/mkusb?action=AttachFile&do=view&target=mkUSB-quick-start-manual-12.pdf)

---

### Post by oldfred on 2017-09-06
First try typing live and then press enter.

See also, syslinux version issue:
[https://askubuntu.com/questions/833422/ubuntu-16-04-not-booting-from-usb-stick-gfxboot-c32-not-a-com32r-image](https://askubuntu.com/questions/833422/ubuntu-16-04-not-booting-from-usb-stick-gfxboot-c32-not-a-com32r-image)

Also may be invalid download.
Often trying different creator for flash drive, or different flash drive may work.

If you only need UEFI boot.
       UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by daniell59 on 2017-09-12
I used the disc creator on an Ubuntu 16.04 DVD. This worked perfectly and I was able to install it on a flash drive. I would like to install Xournal on that flash drive, but I have not been able to. Any advice would be appreciated.

Thanks

---

### Post by sudodus on 2017-09-12
In order to install a program package or tweak the system, so that it survives a reboot, you need an installed system or a persistent live system. [mkusb](https://help.ubuntu.com/community/mkusb) can create a persistent live system of Ubuntu.

---

### Post by daniell59 on 2017-09-12
> **sudodus said:**
> In order to install a program package or tweak the system, so that it survives a reboot, you need an installed system or a persistent live system. [mkusb](https://help.ubuntu.com/community/mkusb) can create a persistent live system of Ubuntu.

Thanks for your assistance. I was able install Ubuntu 16.04 using mkusb. I was able to save documents, but I could not install xournal.

---

### Post by sudodus on 2017-09-12
You need the repository Universe to install xournal. Try the following commands

```
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install xournal
```

---

### Post by daniell59 on 2017-09-12
> **sudodus said:**
> You need the repository Universe to install xournal. Try the following commands

```
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install xournal
```

Thanks. I now have Xournal on my flash drive.

What is repository universe?

---

### Post by sudodus on 2017-09-12
You are welcome :-)

A repository is the place, where program packages are uploaded and new packages replace the old ones, when there are new versions. There are several repositories, 'Main', ... and 'Universe' is one of them. It is 'added', or should I say a pointer to it is added by the add-apt-repository command. Universe is already pointed to in the Ubuntu community flavours, and in standard Ubuntu when installed, but not in live Ubuntu. This is why you had to install it to be able to install its program packages.

If you install the program manager Synaptic, you will get a graphical user interface, where you can look at the repositories in a more intuitive way compared to the command line interface.

```
sudo apt-get install synaptic
```

---

