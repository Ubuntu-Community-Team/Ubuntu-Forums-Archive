---
title: "UEFI &gt; Secure Boot &gt; Ubuntu"
date: 2013-01-15
forum: General Help
---

### Post by Uncle Spellbinder on 2013-01-15
A couple questions:

I have a new computer. HP Pavilion 23-b010 All-in-One Desktop PC, Integrated AMD Radeon HD 7340 graphics, 6 GB memory. Windows 8 pre-installed. UEFI/Secure Boot.
Full specifications here: [http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c03524666&lang=en&cc=us&taskId=135&contentType=SupportFAQ&prodSeriesId=5295897&prodTypeId=12454](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c03524666&lang=en&cc=us&taskId=135&contentType=SupportFAQ&prodSeriesId=5295897&prodTypeId=12454)

1) Is disabling secure boot a wise decision if Windows 8 is installed. I have an option to disable it in BIOS/UEFI, I've just not done it yet.

2) If I decide to wipe my drive and install Ubuntu (or any other distro), is disabling secure boot necessary?&#65279;

---

### Post by oldfred on 2013-01-15
It is all very new. I would not remove Windows at this time. Some systems just work with secure boot on or off, some will work with secure boot off, and some require major work arounds or do not work.

I think you have to at least temporarily disable secure boot to be able to boot from flash drive to install anything. 

       Some general info from oldfred and links.
[http://ubuntuforums.org/showthread.php?t=2086883](http://ubuntuforums.org/showthread.php?t=2086883)

   You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vitial for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Another HP 
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
            UEFI dual boot two drives - HP - before secure boot issues
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)

     HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

    grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Uncle Spellbinder on 2013-01-15
Thanks for the links. I already turned off secure boot. Left the other settings in tact except for boot order. I have DVD drive first. 

I experimented with some live DVDs/Live CDs. So far **no** 32 bit distro will boot (including Ubuntu 12.04, 12.10 and 13.04). All three of these Ubuntu versions in 64 bit are recognized and boot to Live DVD without issue. 

So, now to decide If I want to try to dual-boot or to install and wipe Windows. I've been using Xubuntu and/or Fuduntu on my previous old Dell with no Windows install. Pure Ubuntu. So I really don't *need* Windows. I do have the Windows recovery media in case.

Time to ponder this situation...

---

### Post by offgridguy on 2013-01-15
I always go "ouch" when i see someone wanting to delete something they payed
good money for.  But then i like windows 8. :D

---

### Post by Uncle Spellbinder on 2013-01-16
> **offgridguy said:**
> I always go "ouch" when i see someone wanting to delete something they payed
good money for.  But then i like windows 8. :D

Well, I payed for the PC. Windows 8 just happened to be on it. ;)

In all seriousness, I have the Windows 8 recovery DVDs I made with the HP recovery software. So I won't really lose it. And I've actually grown to appreciate Windows 8. This is my first time dealing with the whole UEFI/Secure Boot thing, so I'll admit to being a bit hesitant. But I really miss Ubuntu and Linux in general. I may just go ahead and back up my pictures, documents and Firefox profile and try and install Ubuntu in place of Windows 8.

---

### Post by perebal on 2013-01-19
> **Uncle Spellbinder said:**
> 
I experimented with some live DVDs/Live CDs. So far **no** 32 bit distro will boot (including Ubuntu 12.04, 12.10 and 13.04). All three of these Ubuntu versions in 64 bit are recognized and boot to Live DVD without issue. 

I have an ACER Iconia W510, which has 32bit ATOM CPU. There is no legacy mode for UEFI in the BIOS SETUP. Is it possible to install somehow Ubintu 32bit on it?

---

### Post by perebal on 2013-01-19
Sorry: Ubuntu :-)

---

### Post by Aergan on 2013-01-19
I found that with my UEFI Dell laptop I had to copy the x64 ISO contents to a Fat32 formatted USB stick. Then it would see the "efi\boot\bootx64.efi"  file and either offer it as boot selection or just auto boot using it.

From there I could either install Ubuntu 12.10 x64 or run the live environment. Unfortunately the only Linux distro that allows me to do this is Ubuntu/Xubuntu even if they support a signed efi file.

---

### Post by mJayk on 2013-01-19
Just installed ubuntu on my GF's HP laptop which came with win 8 pre installed.  

I also had to turn of intel fast boot (I think its called that) aswell.

After that installed fine from USB.

---

### Post by Uncle Spellbinder on 2013-01-19
Needless to say, the more computers are produced with this UEFI, the more will be out there. Growing exponentially. Seems the Linux distro world is going to be forced to adapt to this by having compatible/UEFI-signed media available. Or users of Linux will fall off DRASTICALLY.


[SIZE="1"][COLOR="White"].[/COLOR][/SIZE]

---

### Post by Uncle Spellbinder on 2013-01-23
This is nuts. I've configured BIOS/UEFI, Fast Boot, Legacy and Secure Boot in so many different ways and NONE of them change a damned thing. 

So far not one 32 bit live CD or live DVD distro will boot (including Ubuntu 12.04, 12.10 and 13.04). The only Live media to boot have been 64-bit editions of Ubuntu 12.04/12.10/13.04. And a couple 64-bit Ubuntu-based distros. Other than that, nothing boots. Not Fedora, not OpenSUSE, not SolusOS, not Fuduntu, not PCLinuxOS, not Manjaro, not Gparted...

UN FREAKIN' REAL.


[SIZE="1"][COLOR="White"].[/COLOR][/SIZE]

---

### Post by oldfred on 2013-01-23
I do not think there are any 32 bit versions that support UEFI. UEFI is for newer computers that all are 64 bit capable. No reason for 32 bit.

        The State Of Linux Distributions Handling Secure Boot
[http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI](http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI)

    
You have to have fast boot off. On some systems that may "brick" the system if left on and Windows does not boot. 
       UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)

    
Most have to have secure boot off to install and you have to boot install media in UEFI mode to install correctly. Some report then it just works with secure boot on or off, others have issues.

---

### Post by fuduntu on 2013-01-23
> **Uncle Spellbinder said:**
> This is nuts. I've configured BIOS/UEFI, Fast Boot, Legacy and Secure Boot in so many different ways and NONE of them change a damned thing. 

So far not one 32 bit live CD or live DVD distro will boot (including Ubuntu 12.04, 12.10 and 13.04). The only Live media to boot have been 64-bit editions of Ubuntu 12.04/12.10/13.04. And a couple 64-bit Ubuntu-based distros. Other than that, nothing boots. Not Fedora, not OpenSUSE, not SolusOS, not Fuduntu, not PCLinuxOS, not Manjaro, not Gparted...

UN FREAKIN' REAL.


[SIZE="1"][COLOR="White"].[/COLOR][/SIZE]

Try passing the 'nogpt' parameter to the bootloader when installing 64bit Fuduntu.  When the initial bootscreen appears, press tab and then hit space (if needed) and add nogpt.

---

### Post by Lea Wick on 2013-01-27
"In all seriousness, I have the Windows 8 recovery DVDs I made with the HP recovery software."

Hi, 
I'm new to Ubuntu and fairly new to computers. I also have windows 8 preloaded on my PC and would like to keep it while trying Ubuntu. Where did you get that HP recovery software? Are they bootable recovery DVDs? 
Thanks

---

