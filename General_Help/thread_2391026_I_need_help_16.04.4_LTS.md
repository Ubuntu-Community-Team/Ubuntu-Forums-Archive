---
title: "I need help 16.04.4 LTS"
date: 2018-05-05
forum: General Help
---

### Post by joseprodri56 on 2018-05-05
I have a laptop intel travelmate b115 series, and I have problems with Ubuntu 16.04.4 LTS. I open the installation with a USB drive, and always that I open the installation, the ubuntu installation closes, and an error appears saying "system programs problem detected, do you want to report the problem now?", and it directs me to the ubuntu desktop. I try all, comands, installing grub, uninstalling windows, format the disk via UEFI, and I install de steamOS, and this OS it "bugs" me. I know there's an update that was made recentlywas recently put, but the same will happen to me.
If anyone don't understand me, it's my english, i'm from spain, but i need help.

---

### Post by Autodave on 2018-05-05
When the message appears asking you if you want to report the problem, say YES and then look at the "details" and see what it says. That will help figure out what is going on.

Did this setup ever work in the past?

---

### Post by joseprodri56 on 2018-05-06
I try with this setup, but i try to fix with this setup, but it doesn't solve it.
The error say:
Sorry, Ubuntu 16.04 has experienced an internal error.
If you notice further problems, try restarting the computer.
```
ExecutablePath
   /usr/lib/ubiquity/bin/ubiquity
Package
   ubiquity 2.21.63.6
ProblemType
   Crash
Title
   ubiquity crashed with signal 7 in FT_Load_Glyph()
ApportVersion
   2.20.1-0ubuntu2.15
Architecture
   amd64
Casper
   ........ Writing new source list
   Source list entries for this disc are:
   deb cdrom:[Ubuntu 16.04.4LTS _XenialXerus_-Release amd64 (20180228)]/ xenial main restricted
   Repeat this process for the rest of the CDs in your set.
CasperVersion
   1.376.2
CoreDump
   (binary data)
Date
   Sun May 6 09:08:21 2018
Dependencies
   ........
Disassembly
   => 0x7f2664acec50:   movzbl (%rdx),%eax
   Etc.....
DistroRelease
   Ubuntu 16.04
InstallCmdLine
   BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
InterpreterPath
   /usr/bin/python3.5
Journal error (errors from bluetooth, hostname anf network manager)
LiveMediaBuild
   Ubuntu 16.04.4 LTS "Xenial Xerus" - Release amd64 (20180228)
PackageArchitecture
   amd64
ProcCmdline
   /usr/bin/python3/usr/lib/ubiquity/bin/ubiquity --only
ProcCpuinfoMinimal (i have an intel celereon N2940 @ 1.83GHz)
```

---

### Post by rohitsuman86 on 2018-05-06
Ubuntu 16.04 is OLD and so it's installer. Installer that came with Ubuntu 16.04 was very buggy and crashed in many configurations all the time.

In your case also, the installer had crashed. It had problems in my PC too.

Why don't you and download and install Ubuntu 18.04 LTS instead? It's miles ahead of 16.04 in every way.

---

### Post by joseprodri56 on 2018-05-06
I don't know why, but i try to install the ubuntu in vurtualbox (with other computer, i have 2 computers), and all good, and i go to install the ubuntu in my laptop without virtualbox (it's faster than windows 10), and so i am.
I'm going to install it, I'll say something

---

### Post by rohitsuman86 on 2018-05-06
> **joseprodri56 said:**
> I don't know why, but i try to install the ubuntu in vurtualbox (with other computer, i have 2 computers), and all good, and i go to install the ubuntu in my laptop without virtualbox (it's faster than windows 10), and so i am.
I'm going to install it, I'll say something

This is exactly what I'm saying, installer of 16.04 is buggy. It has problems with different configurations and you will never know what it has problems with.

When running in VirtualBox, different emulated hardware of VirtualBox is detected. That's why it works in it.

Install Ubuntu 18.04 LTS. 

If you want to install 16.04 LTS only, then install Linux Mint 18.3. It's installer is way less buggy than Ubuntu 16.04 installer. It's also based on Ubuntu 16.04 LTS.

I will still recommend : Install Ubuntu 18.04 LTS.

---

### Post by joseprodri56 on 2018-05-06
I don't know why, but i try to install the ubuntu in vurtualbox (with other computer, i have 2 computers), and all good, and i go to install the ubuntu in my laptop without virtualbox (it's faster than windows 10), and so i am.
I'm going to install it, I'll say something

---

### Post by joseprodri56 on 2018-05-06
Sorry, i say the same

---

### Post by joseprodri56 on 2018-05-07
I have another error, saying:
The installer found a error while copying the files to the hard drive
[Erno 5] Input/output error
The specification is in spanish:
A menudo, esto se debe a un disco o unidad de CD/DVD defectuosos, o bien a un disco duro defectuoso. Puede probar a limpiar el CD/DVD, grabar el CD/DVD a menos velocidad, limpiar la lente de la unidad de CD/DVD (en tiendas de electrónica puede encontrar kits de limpieza), comprobar si el disco duro es viejo y necesita ser sustituido, o mover el aquipo a un entorno mas fresco.
In sumary, the USB is defective, and try to buy another one or repair, or cleaning of virus.
When I install the steamOS in my computer, I had no problem, only one of the operating system itself. And I have mounted the USB bootable with rufus, and I check the option "search damaged blocks in the USB", with the 4 steps.
I think, the problem is in computer.
And what I do not understand is that it tells me this error, and when I try again to install the ubuntu, it tells me that the hard drive already contains the ubuntu.
Pd: I am talking from ubuntu 18.04
Repeat, If anyone don't understand me, it's my english

---

### Post by joseprodri56 on 2018-05-09
Pls, I don't know how solve this error

---

### Post by rsteinmetz70112 on 2018-05-09
Your error message says that the CD/DVD is defective. If you are using a DVD make and try a new DVD. If you are using a USB drive check the drive then download and make a new image.

It is possible the DVD drive and or the USB port are defective, if you have another one try that. There is also a network installer that will download most of the software over the Internet.

I have installed 16.04 LTS many times and have never really had a problem. I usually use a DVD.

Does your install media allow you to "Try" Ubuntu and does it work? If so that is a pretty good indication your hardware is detected and working.

If you can start your Ubuntu installation and get to a console login or repair prompt run:

```
sudo --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

---

