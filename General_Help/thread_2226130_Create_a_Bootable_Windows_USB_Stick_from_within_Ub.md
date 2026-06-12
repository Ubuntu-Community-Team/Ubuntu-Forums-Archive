---
title: "Create a Bootable Windows USB Stick from within Ubuntu"
date: 2014-05-25
forum: General Help
---

### Post by evan12 on 2014-05-25
Hello all, I have a question that I'm hoping somebody here can help me solve. I am trying to make a bootable copy of Windows 7 from within Ubuntu. That is, I have a copy of the Windows 7.iso (Just purchased yesterday) and I want to put it onto a USB stick and install it onto my computer.

The problem is, I have been having an extreme degree of difficulty trying to get this to work. All of the ways online have failed me at one point or the next, and I'm ready to just break down and go purchase some blank DVD-RW's. I have tried WinUSB, unetbootin, and the terminal for making a bootable flash drive and all have either not worked or the methods are so outdated they can no longer even be used in the same way.

There must be somebody out there who has done this before, and if so, PLEASE give me some detailed insight on how you managed to accomplish it.

Note: I am on a very beginner's level with Linux, the terminal baffles me most of the time, so if this needs to be done on a command line basis, please be VERY VERY detailed and simple in your instructions. People seem to have a habit of putting  sudo <insert filepath> <insert whatever> <insert something else> <potato> into their instructions and just lose me. My flash drive is labeled /dev/sdf1 according to the terminal and my .iso file is labeled win7.iso. If you would use these parameters when issuing instructions (should that actually happen) I'd really appreciate it.

Thanks guys. And apologies if this is in the wrong category, I honestly don't know what this falls under as far as support.

---

### Post by LastDino on 2014-05-25
What version of Ubuntu do you've?

You can try making W7 bootable by WinUSB software. 
[http://en.congelli.eu/prog_info_winusb.html](http://en.congelli.eu/prog_info_winusb.html)
PPA For: 13.10, 13.04, 12.04, 12.10

```
sudo add-apt-repository ppa:colingille/freshlight
sudo apt-get update
sudo apt-get install winusb
```


For 14.04

```
sudo add-apt-repository ppa:colingille/freshlight
sudo sh -c "sed -i 's/trusty/saucy/g' /etc/apt/sources.list.d/colingille-freshlight-trusty.list"
sudo apt-get update
sudo apt-get install winusb
```

This is curtsy of someone on ask Ubuntu. 

I've personally only used Unetbootin to make Windows bootable on Linux and it has never really failed me. 
Are you sure you're following the procedure correctly? Are you formatting USB to FAT32 before doing anything to it with whatever software you are using?

---

### Post by evan12 on 2014-05-25
> **LastDino said:**
> What version of Ubuntu do you've?



I'm running Ubuntu 14.04

> 
You can try making W7 bootable by WinUSB software. 
[http://en.congelli.eu/prog_info_winusb.html](http://en.congelli.eu/prog_info_winusb.html)
PPA For: 13.10, 13.04, 12.04, 12.10

```
sudo add-apt-repository ppa:colingille/freshlight
sudo apt-get update
sudo apt-get install winusb
```


For 14.04

```
sudo add-apt-repository ppa:colingille/freshlight
sudo sh -c "sed -i 's/trusty/saucy/g' /etc/apt/sources.list.d/colingille-freshlight-trusty.list"
sudo apt-get update
sudo apt-get install winusb
```

This is curtsy of someone on ask Ubuntu.


I've tried WinUSB, but unfortunately, it cannot find my USB drive no matter what I do. (The USB drive is recognized by everything else, however, so it isn't the problem.

> 
I've personally only used Unetbootin to make Windows bootable on Linux and it has never really failed me. 
Are you sure you're following the procedure correctly? Are you formatting USB to FAT32 before doing anything to it with whatever software you are using?

Further research into Unetbootin revealed that newer versions do not support making a Windows install. For whatever reason, this usage was removed or simply is no longer supported. I believe Windows 7 requires an NTFS format as well, not a FAT32 format, although I'm not entirely sure.

But honestly, no, I'm not entirely sure I'm doing any of this correctly.

---

### Post by LastDino on 2014-05-26
That is a known problem and there is workaround for that:

[http://askubuntu.com/questions/162174/how-do-i-use-unetbootin-to-make-a-bootable-windows-usb-installer](http://askubuntu.com/questions/162174/how-do-i-use-unetbootin-to-make-a-bootable-windows-usb-installer)

Is this not working for you?

Or get different version of Unetbootin and follow this.
[http://www.linuxandlife.com/2012/12/unetbootin-create-bootable-usb-windows-7.html](http://www.linuxandlife.com/2012/12/unetbootin-create-bootable-usb-windows-7.html)

---

