---
title: "Can I install Ubuntu in Windows 8"
date: 2015-05-08
forum: General Help
---

### Post by Jonatan Formentera on 2015-05-08
My computer has broken down and I want to buy another one, but now all computers are with Windows 8. I'd like to know if I can install Ubuntu in it. Another question. If I buy a computer with a Celeron processor and 4 GB memory Ram, what kind of OS must I install, for 34 or 62 Bytes?
Thanks

---

### Post by 8bit-lucifer on 2015-05-08
Yes you can install Ubuntu on a Windows 8.1 computer unless that computer runs an arm processor (with is very unlikely).
Question number two, I need to know with Celeron processor your talking about, Intel makes many Celeron processors [http://en.wikipedia.org/wiki/List_of_Intel_Celeron_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_Celeron_microprocessors)
Having said that, it´s very unlikely you buy a 32-bit PC in 2015.

---

### Post by grahammechanical on 2015-05-08
We cannot install Ubuntu _in_ Windows 8. There used to be a method for installing Ubuntu in earlier versions of Windows but that method is not compatible with Windows 8 and therefore it is no longer under development.

As already stated we can install Ubuntu in a dual boot configuration _on_ a Windows 8 machine. These are the important matters that we need to keep in mind.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If we decide to create space for Ubuntu by resizing the Windows partitions then it is important to keep in mind that before we resize any Windows partitions we defrag and restart Windows more than once and then we use Windows utilities to resize and move Windows partitions to create unallocated space to use for Ubuntu partitions to install Ubuntu in.

There is also a method of installing Ubuntu that first of all erases the entire contents of the hard disk and starts from the beginning with only Ubuntu on the machine.

Regards.

---

### Post by mattharris4 on 2015-05-09
Unfortunately Ubuntu cannot be installed inside of Windows.  I would dual-boot.  **_However, I do warn you that it is very difficult to install any Linux OS on HP computers with Win 8.1 pre-installed.  If you want to run Linux (of which Ubuntu is one OS using that kernel) DO NOT purchase an HP computer with Win 8 or 8.1 pre-installed on it._**  You will have nothing but grief attempting to install and run Ubuntu on it.  A couple of posters have had trouble with some very new Toshibas as well although my year old Toshiba laptop took Lubuntu without major issue. ** Reports show Dells and Lenovos usually take a Ubuntu install relatively well** (Dell actually sells computers with Ubuntu pre-installed but unfortunately they are i7 monsters that cost $1300 plus, I don't recommend spending that kind of coin on a new computer nowadays), instructions on a dual-boot install with Win 8.1 are available on the Ubuntu user support website.  Fast Boot must be disabled in the UEFI, sometimes there are a couple of other minor steps in the UEFI but with a Dell (other than maybe the 2 in 1 laptops) and a Lenovo you should not have much trouble with the install as long as you can follow instructions.  Dell has i3 equipped laptops with 4GB of RAM for less than $500 ([www.dell.com/deals](www.dell.com/deals)).  Lenovos can be purchased from several web-based computer sellers, Newegg and Tiger Direct being two (if you want a new computer and not a refurbished one be sure to check the condition in the description).  There isn't anything inherently wrong with a refurb but the chance of a defective computer increases with one and you would likely be purchasing a three year old computer.  Purchasing a refurb is one way to get out of dealing with the issues that installing Ubuntu on an UEFI computer but with a Dell or a Lenovo that isn't as much of an issue.

Another option is to buy a computer from a seller that pre-installs a Linux OS onto it for you.  Linucity ([www.linucity.com](www.linucity.com)) and System 76 ([www.system76.com](www.system76.com)) are reasonably well regarded, the former has a better selection and lower prices and any computer either advertises (when I last checked earlier this week) comes with a minimum 4GB of RAM and an i3 processor or better.  There are some newer sellers, Current Build is an interesting one as they sell some lower priced computers (at least for pre-installed Linux computers) with your choice of Linux OS pre-installed ([www.currentbuild.com](www.currentbuild.com)) although I don't know of anyone that has used them so I cannot vouch for them at all.  They say they will customize a computer to your specs, they have a computer advertised that sells for $289 but the processor is a slower, lower capacity, cheap Celeron CPU that I would upgrade with something faster like an Intel i3 (or the AMD equivalent) and I would also upgrade the included 2GB RAM to 4GB.  Of course that would significantly raise the price of the computer but I think if you go that route you would be happier with the computer if you spent the extra dough and had them install a better processor and more RAM in it, Ubuntu can be painful to run on less than 2.5GB of RAM, they do not advertise installing any light Linux OSes.  They do claim to customize so they might install Lubuntu if they were asked -- I don't know, Lubuntu will run well on almost any recent processor and only requires 1.5GB of RAM maximum for basic web browsing, word processing and music/video/DVD playing.  They have several models but most of them as advertised come with crappy processors that I would strongly recommend upgrading to at least an i3.  Even their $589 model comes with a Pentium G3258 processor which would probably serve you fine now (my eight year old desktop -- not from any Linux seller -- has a predecessor Pentium 4 that does fine for web browsing, word processing, music listening and video watching -- the processor with their $589 advertised computer should run even better) but in 4-5 years you may be wishing for a faster processor if you do picture editing, video editing, etc. with it.  They have a $1500 model that is fully loaded with an i5 CPU and 8GB RAM but there is no need to spend that much.

---

### Post by dragonfly41 on 2015-05-09
> 
My computer has broken down and I want to buy another one, but now all computers are with Windows 8. I'd like to know if I can install Ubuntu in it.


Re: your first question what actually do you mean by "broken down"?  If it is a faulty drive you can just buy a new drive and install Ubuntu.  
Cheaper to recycle than buying a new computer.  You might also be able to repair a "broken" disk and scrub the pre installed windows for installation of Ubuntu (or variant).

You will need to borrow another pc to

[LIST]
[*]download a Ubuntu distro 
[*]burn to an external flash drive (I use an 8 GB flash drive to hold my LiveUSB for such reinstallations). 
[/LIST]


Finally if you do decide to buy another pre-installed windows pc there is the option of installing VirtualBox.com on windows and then install Ubuntu as a virtual machine on VirtualBox.   You will need plenty of RAM for this option or performance will be sluggish .. but it can be a middle road for learning Ubuntu before you decide to install Ubuntu on raw drive.

You can also install Ubuntu to boot from another drive in a USB container.  This would allow you to keep the preinstalled windows in internal drive and optionally boot up Ubuntu (if your BIOS boot options allow booting from USB).

[p.s.]
Read this sticky thread on recycling old computers.
[http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

---

