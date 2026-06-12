---
title: "Ubuntu on Asus P5Q mobo -- cannot see hard drive or network card"
date: 2008-07-06
forum: General Help
---

### Post by Halsafar on 2008-07-06
I have loaded up live discs, text installers, both feisty and hardy heron.  Nothing can seem to recognize my motherboards network card (Atheros AR8121/AR8113 PCI-E Ethernet Controller is what Vista sees).  

More importantly, Ubuntu cannot recognize my hard drives, period.  I think this has something to do with MARVEL.  I am at a complete loss.

I just picked up this machine, the motherboard seems to be the major issue here.  

- Intel Core 2 Quad Q6600
- Asus P5Q (not pro, not deluxe, just P5Q)
- 4GB OCZ Ram (2x2GB)
- Seagate 500GB HD

So basically, text installer can get as far as attempting to find my hard disk at which point it gives me a giant list of drivers to choose from.  Any help?

Thanks,
Stephen Damm

---

### Post by Halsafar on 2008-07-06
*bump* This is ridiculous, no answers anywhere.

---

### Post by wamgrays on 2008-07-07
Hi - basically I have the same problem:

- P5Q Deluxe
- Seagate 1TB SATA
- Pioneer Bluray SATA

Some notes:
- Live CD will not boot from the Bluray drive - had to attach a CD drive to the IDE and run the Alt installer. It did not see the hard drive but when I told it to use the generic IDE it found it and was quite happy to do the rest of the install. Now the problem is it won't boot (locks on splash screen and eventually ends up in busybox). I have tried passing all-generic-ide as parameter to kernel in Grub without success.
- The latest version of sysrescuecd (1.0.4) boots OK (on Bluray - device name assigned is something like sr0) and sees the hard drive as sda.
- have set BIOS SATA Configuration to Compatible, IDE

I must admit I am a bit surprised to have this sort of trouble these days - it's not like SATA is all that new - been around for a few years now. What IS cool about this motherboard, is the Express Gate - OS on flash. I'm doing this post on the built-in browser without any OS installed on my disk.

---

### Post by wamgrays on 2008-07-08
Check this thread on the Asus site - seems fairly helpful: [http://vip.asus.com/forum/view.aspx?id=20080624021821000&board_id=1&model=P5Q&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20080624021821000&board_id=1&model=P5Q&page=1&SLanguage=en-us)

I have just changed the BIOS setting for SATA config from IDE to AHCI and my install has booted up OK.

---

### Post by wamgrays on 2008-07-15
A further update:

AHCI didn't work out.
Set back to IDE/Enhanced
- able to boot 1.0.4 of sysrescuecd
- NOT able to boot Mythbuntu live disk - after the first menu - (8.04) BUT by setting kernel boot parameter (generic.all_generic_ide=1) was able to boot and install OK.
- got basic system going BUT playing DVD was jerky. After a bit of a google appears it MAY be due to all_generic_ide (ahhhhh!!)

the saga continues ...

---

### Post by father on 2008-07-16
Same problem... with P5Q Pro (2G RAM, 3 SATA HDD and one SATA ASUS DVD-RW) and Hardy (or even Fedora...)

I've just setting SATA as AHCI and disable the Marvel and now Ubuntu boot from LiveCD and seen all of my SATA HDD by gparted...

Good luck!

---

### Post by wamgrays on 2008-07-16
Thanks for the feedback. Not sure exactly what you meant by "disable the Marvel". I tried AHCI and switched Marvel IDE Boot ROM to disabled but still wouldn't boot the live CD (64bit).

---

### Post by ydrol on 2008-07-17
Snap (but with Mandriva). 
Just hoping we can get some momentum behind this so it gets fixed upstream before all Autumn/Fall releases of our favourite distros..

[http://forum.mandriva.com/viewtopic.php?p=519755](http://forum.mandriva.com/viewtopic.php?p=519755)

Still not sure when a very old verision of Windows 2003 Server R2 SP1 can load happily and all new Linux distros struggle. (I suspect Windows is being blissfully ignorant of something :) )

---

### Post by father on 2008-07-19
I'm still in trouble with the installation...:mad:

However should be there a solution... I've just installed the ExpressGate (from Win...) And it works without any BIOS or without another hacks... and yes it's a Linux based something... 

:confused: Any idea?

---

### Post by lordalbert on 2008-07-24
> **father said:**
> I'm still in trouble with the installation...:mad:

However should be there a solution... I've just installed the ExpressGate (from Win...) And it works without any BIOS or without another hacks... and yes it's a Linux based something... 

:confused: Any idea?

what's the problem?
If you enable AHCI your hd works?

---

### Post by richard.e.morton on 2008-08-07
Hi All,

I have a similar issue, any help would be gratefully received.

I am trying to install LInuxMCE which requires Kubuntu 710 on a P5Q

Ethernet doesn't work
SATA drives are not recognised
I've not got as far as Audio yet...

Thanks

R

---

### Post by brunod on 2008-08-12
bleh. I have the same problem, Asus P5Q, I've tried two hard drives, a WD 500GB and a Seagate 500GB both are not seen by gparted on step 4 of install (Ubuntu 8.04). 

The irony is that I've just built this PC to replace two others, one of which is an old linux fileserver the other being my main machine on WinXP, and I wanted to switch to Ubuntu...

---

### Post by d0b33 on 2008-08-18
Same problem...

I was hoping to install linux but will have to figure this out first looks like it.

---

### Post by d0b33 on 2008-08-18
Fixed!

As mentioned earlier the solution is to choose AHCI not IDE under storage configuration :)


Problem now is that Vista gives me a BSOD and cant install or startup so I have to choose IDE for it to work :(

---

### Post by janlazar2 on 2008-08-22
thank you for this, it was very helpfull.
i can install ubuntu 8.4 now
by the way, what the AHCI mod actully is?

---

### Post by d0b33 on 2008-08-22
> **janlazar2 said:**
> thank you for this, it was very helpfull.
i can install ubuntu 8.4 now
**by the way, what the AHCI mod actully is**?

It is **Advanced Host Controller Interface**, enables NCQ and hot plugging and is recommended over IDE.

[http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface)

---

### Post by quill7111 on 2008-08-26
> What IS cool about this motherboard, is the Express Gate - OS on flash. I'm doing this post on the built-in browser without any OS installed on my disk.

I've been unable to install Expressgate since I'm not running windows at all. I'm curious if you had to install it yourself or whether it just worked from the beginning. 

On another note, I've not really had any install issues on my P5Q with two 750GB SATA HDDs (AHCI mode), IDE CD/DVD-RW. I needed to use the alternate desktop to set up the RAID scheme I wanted, but the LiveCD recognized everything just fine. Maybe that problem has simply been addressed in the last six weeks, but I thought I'd pass on my positive experience. If anyone has an answer on how I can get Expressgate installed without windows, I'd love to hear it. Thanks!!

---

### Post by NineseveN on 2008-08-27
> **quill7111 said:**
> I've been unable to install Expressgate since I'm not running windows at all. I'm curious if you had to install it yourself or whether it just worked from the beginning. 

---

If anyone has an answer on how I can get Expressgate installed without windows, I'd love to hear it. Thanks!!


On the higher end models of this series of mobo, Expressgate is installed on a ROM chip directly on the mainboard. On the lower end models, it requires a disk install, which mostly negates the benefits.

---

### Post by d0b33 on 2008-08-27
When I launched the live CD the first time and had my SATA drives set to IDE and not AHCI ubuntu detected the 500MB free needed to install expressgate, I never bothered installing to the slot but maybe someone good give it a shot?

---

### Post by NineseveN on 2008-08-27
> **d0b33 said:**
> When I launched the live CD the first time and had my SATA drives set to IDE and not AHCI ubuntu detected the 500MB free needed to install expressgate, I never bothered installing to the slot but maybe someone good give it a shot?

Expressgate, AFAIK, can only be run from IDE at present.

---

### Post by d0b33 on 2008-08-27
> **NineseveN said:**
> Expressgate, AFAIK, can only be run from IDE at present.

Yup that's what I meant... in IDE mode ubuntu detected my expressgate slot, I wonder if it's possible to install ubuntu to it?

---

### Post by pigeonjim on 2008-09-11
I love my p5q deluxe however I too cant get Ubuntu to install; It doesnt see my sata hard drive. :-(
I can not change to ahci in the bios because i already have xp installed (which i use for games) and I didnt do the F6 thing because I dont have a floppy drive. I have tried and failed to use many methods to change my xp to ahci without reinstalling and I have been unsuccessful.
Is there any other way to get Ubuntu to recognise my hard drive so I can install?

---

### Post by d0b33 on 2008-09-11
> **pigeonjim said:**
> I love my p5q deluxe however I too cant get Ubuntu to install; It doesnt see my sata hard drive. :-(
I can not change to ahci in the bios because i already have xp installed (which i use for games) and I didnt do the F6 thing because I dont have a floppy drive. I have tried and failed to use many methods to change my xp to ahci without reinstalling and I have been unsuccessful.
Is there any other way to get Ubuntu to recognise my hard drive so I can install?

I had a similar problem with Vista and had to apply a reg tweak according to microsoft support then install the intel matrix storage software and this allowed me to use AHCI without having to reinstall, maybe it's possible with XP?

Vista runs much better under AHCI ;)

Maybe install these drivers and see what happens?
[http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=2101](http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=2101)

---

### Post by pigeonjim on 2008-09-12
I have tried to install the intel drivers using different methods but it doesnt work :-(

---

### Post by d0b33 on 2008-09-12
> **pigeonjim said:**
> I have tried to install the intel drivers using different methods but it doesnt work :-(

This is what worked for me using Vista, I posted this in the ASUS forums...
> Nevermind the fix is very simple, just follow this....
[http://support.microsoft.com/kb/922976](http://support.microsoft.com/kb/922976)

To resolve this issue, enable the AHCI driver in the registry before you change the SATA mode of the boot drive. To do this, follow these steps:
1.	Exit all Windows-based programs.
2.	Click Start, type regedit in the Start Search box, and then press ENTER.
3.	If you receive the User Account Control dialog box, click Continue.
4.	Locate and then click the following registry subkey:
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Msahci
5.	In the right pane, right-click Start in the Name column, and then click Modify.
6.	In the Value data box, type 0, and then click OK.
7.	On the File menu, click Exit to close Registry Editor.


This is for Vista but maybe Microsoft has a similar fix for XP?

---

### Post by d0b33 on 2008-09-13
Be sure that your SATA drive is plugged into the intel ports(red) not the orange and white Silicon Image ports, AHCI does not work for these ports.

---

