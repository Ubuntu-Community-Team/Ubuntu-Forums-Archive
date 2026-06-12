---
title: "No USB Drive, need to install Ubuntu (HELP)"
date: 2021-07-25
forum: General Help
---

### Post by teehee2 on 2021-07-25
Hey, so I'm having this dilemma of not being able to find a program that can install Ubuntu on my Windows drive. I would just normally install via Flash drive but I can't find any and need to have this done by morning. I'd appreciate help.

---

### Post by C.S.Cameron on 2021-07-25
Do you have a Android phone? DriveDroid will let you use your phone as a USB drive.

Alternatively:

Some people have luck with UNetbootin Frugal mode, which installs Ubuntu Live to a corner of your C drive.

---

### Post by TheFu on 2021-07-25
Use a virtual machine. Install virtualbox into the current OS, then create a VM and use the ISO file from the links in the page header here to download xubuntu/lubuntu/ubuntu-mate.  Avoid the Gnome3 ubuntu (which is the default), since it doesn't run well inside a VM or on minimal systems.

Or you could burn an ISO file onto DVD media and use that to install, if you like.

The virtual machine solutions is much more flexible and much less dangerous than a physical installation. I'd recommend that 90% of the time over any sort of multiple install.

You can also use SDHC or microSD devices if the system supports those for boot. Most do. Every laptop I've had since at least 2009 has.  A few yrs ago I stopped buying USB flash drives and started buying only Class10 or faster microSD cards.  Then I bought a few microSD -to- USB3/3.2 adapters ($9), so any microSD can be used just like a USB flash drive.  Very flexible.

---

### Post by grahammechanical on 2021-07-26
I am confused. Why can you not follow these instructions?

[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)

To put things briefly

1) In Windows download the Ubuntu ISO image.
2) In Windows install an application called Rufus.
3) Use Rufus to burn the Ubuntu ISO to the USB stick.
4) Boot into Ubuntu on the USB stick
5) Use the Ubuntu installer program to install Ubuntu on your hard drive.

I have a feeling that you also need to read these two guides

[https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started)

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

Regards

---

### Post by TheFu on 2021-07-26
Simply a lack of physical USB device availability.

I think the OPs issue is that no free USB storage is available and the idea of moving files off a stick temporarily, using the stick with rufus, doing the install, then moving the files back never came up?  But IDK.

---

### Post by dragonfly41 on 2021-07-26
> [COLOR=#000000]that can install Ubuntu on my Windows drive.[/COLOR]

If you have Windows 10 then Ubuntu is already on your drive.
It is named WSL or later version WSL2.

And you can run Linux apps in RollApp.com if it is a temporary requirement.

---

### Post by mIk3_08 on 2021-07-26
> **teehee2 said:**
> Hey, so I'm having this dilemma of not being able to find a program that can install Ubuntu on my Windows drive. I would just normally install via Flash drive but I can't find any and need to have this done by morning. I'd appreciate help.

I assumed that you know already how to run Linux Ubuntu iso Installer so, what you need to do is to look for additional partition disk on your MS Windows drive.
 
And I assumed that your MS Widows Disk was not partition yet then look for Partition Management Software so that you can successfully add partition on your MS Windows disk
When you already successfully added a partition to check it, just go to the administrative tools under your windows control panel then on the computer management
choose Storage then Disk Management there you can see your new created partition.

But if your disk is already partitioned you will just choose your additional partitioned disk Local Disk Drive D: for your Linux Ubuntu Installation. 
If you have important Files on your Local Disk Drive D: and you still have space on your Local Disk Drive C: then just transfer it from 
Local Disk Drive D: to Local Disk Drive C: which is your MS Windows System Drive

Just be careful of choosing which partition you install your Linux Ubuntu System 
or you can just simply choose the install Ubuntu alongside with your MS Windows 
[Click Here]("https://help.ubuntu.com/community/Installation") for you installation Guide

[Click Here]("https://ubuntu.com/download/desktop") To Download the Linux Ubuntu ISO to be put into USB or just write it directly if you have the DVD/CD Disk Writer/Burner.

---

