---
title: "How to make a UEFI bootable usb memory stick?"
date: 2019-03-20
forum: General Help
---

### Post by mdurham on 2019-03-20
Hi each, 
My Acer A515-52 bios does not allow booting except with UEFI. 
How can I make a UEFI bootable mem stick from an ISO file? In particular I want to make a bootable stick with "redobackup.ISO". Is it even possible? 
Why would ACER do such a crazy thing? There is no way to boot non UEFI usb sticks.

Cheers, Mike

---

### Post by westie457 on 2019-03-20
Will this help you create the iso you require? 
[https://chrtophe.developpez.com/tutoriels/redobackup-upgrade-and-live-creation/](https://chrtophe.developpez.com/tutoriels/redobackup-upgrade-and-live-creation/)

To burn the iso to USB in Windows use Rufus [https://rufus.ie/](https://rufus.ie/) 
or Etcher [https://www.balena.io/etcher/](https://www.balena.io/etcher/)

To burn the iso in Linux use Etcher link above or Mkusb [https://www.balena.io/etcher/](https://www.balena.io/etcher/)

---

### Post by oldfred on 2019-03-20
Is redobackup.iso UEFI bootable? If not created as UEFI bootable, then it will never work.
It says based on Ubuntu and Ubuntu has been UEFI bootable for 5 years.

But you can just use Ubuntu and its backup or add other backup tools.
       Also link on how to create a  bootable DVD or USB flash drive, using Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
Direct link to downloads page, most want  ubuntu-18.04-desktop-amd64.iso
[http://releases.ubuntu.com/18.04/](http://releases.ubuntu.com/18.04/)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

Only some 32bit UEFI systems have been UEFI only so far. Intel recommendations for 2020 are that the CSM mode be obsoleted or no BIOS boot.
       
  CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    Systems since 2012 have been UEFI since Windows required vendors to install Windows in UEFI boot mode.

Your Acer may just need you to set UEFI password to change boot mode. But better to use UEFI anyway.
        
 Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator)

---

### Post by sudodus on 2019-03-20
I think **Redo backup** is too old to work in UEFI mode. It boots only in BIOS mode. I tested

- cloning

- making a persistent live drive with mkusb

Newer versions of 32-bit Ubuntu and Ubuntu community flavours can boot in UEFI mode, when made persistent live with mkusb, but it does not work in this case. Well, it boots, but does not find the linux kernel files, so the boot structure is modified from that of Ubuntu or from a too old version of Ubuntu.

I suggest that you look for a tool with a current version for your backup.

There are several alternatives: [help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

If you want a cloning alternative, I would recommend [Clonezilla](https://clonezilla.org)

[hr][/hr]
As indicated by oldfred, you might be able to boot your Acer in BIOS mode. But even in this case, I would suggest that you use a more modern tool.

---

### Post by mdurham on 2019-03-20
Thanks for your help guys.
I had no luck with this. Unfortunately This Acer is locked on UEFI mode, there is no way to change it, apart from new bios firmware I suppose. hahaha
Thanks again, Mike

---

