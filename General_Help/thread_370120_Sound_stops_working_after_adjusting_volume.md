---
title: "Sound stops working after adjusting volume"
date: 2007-02-25
forum: General Help
---

### Post by Roel123 on 2007-02-25
Hello,

I have a rather weird sound problem. The sound works fine until I touch the volume. The volume slider bar in  Totem works but if I touch the 'master' volume slider (the speaker icon in the taskbar) my sound is gone. Same if I adjust the sound using the Fn-key on the laptop, touch it and no more sound.

Can anyone help me with this? Or at least tell me how I can restart just the sound (I don't want to reboot my laptop everytime I want to hear something).

OS: Ubuntu 6.10 fully up to date
PC: Asus VX1

lspci:

> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d8 (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

I've been using Linux for some time now but I'm not an expert.

---

### Post by energiya on 2007-02-25
> **Roel123 said:**
> 
Can anyone help me with this? Or at least tell me how I can restart just the sound (I don't want to reboot my laptop everytime I want to hear something).


To restart alsa:
```

sudo /etc/init.d/alsa-utils restart

```

I don't know how to help more...

---

### Post by Roel123 on 2007-02-25
Thank you, that gives me back some noise but only on the right channel. The left is muted. Both levels are up in the mixer, they are linked together but on the left it's absolute silence.

It goes something like this:

booting -> works fine
adjusting volume -> no more sound
restarting alsa-utils -> only sound on the right, none on the left

This is very annoying, guess I wont be be using that expensive thing for anything fun.

---

### Post by Billy McCann on 2007-02-28
> **Roel123 said:**
> Hello,

I have a rather weird sound problem. The sound works fine until I touch the volume. The volume slider bar in  Totem works but if I touch the 'master' volume slider (the speaker icon in the taskbar) my sound is gone. Same if I adjust the sound using the Fn-key on the laptop, touch it and no more sound..

Roel,

Funny.  I've been having the same problem.  And I use an Asus motherboard.  And I have an ICH7 family Intel audio device.  Maybe it's a hardware thing?  

A strange thing that mine does.  The panel applet won't allow me to adjust the volume.  I can pull it down, but it'll snap back to 100% even while I'm holding down the left-click.   If I drag it all the way down, it'll do a dance between both ends.  Sort of amusing ... for a moment.  

Maybe some kind soul out there knows the solution.  I take it you've searched google + forums for this and got nada.  Me too.

---

### Post by kolach on 2007-02-28
Hi, all!
I have an ICH7 family Intel audio either.
And the same problem :(

---

### Post by Billy McCann on 2007-02-28
> **kolach said:**
> Hi, all!
I have an ICH7 family Intel audio either.
And the same problem :(
Come join the pity party!

:cry:

---

### Post by kolach on 2007-02-28
:)
Found a solution, 
at least it worked for me:
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

I've updated to the latest version of alsa and it worked!

---

### Post by Roel123 on 2007-02-28
I followed the instructions on that page but it does not solve my problem.

---

### Post by Billy McCann on 2007-03-01
I use ubuntu 6.10, so I only followed the "for every Linux" instructions.  Didn't work.

Ya think maybe upgrading to Feisty might help?

---

### Post by kolach on 2007-03-01
> I use ubuntu 6.10, so I only followed the "for every Linux" instructions. Didn't work.
I use 6.10 either, 
but I did as it was written for Ubuntu 6.06 LTS and it worked

---

### Post by Billy McCann on 2007-03-01
Well, I take it back.  I used the "every Linux" and, once I restored my BIOS to normal, the sound will play in my left ear.  But in my right ear, boy oh boy, ... let's just say I'm glad that I didn't have it turned up too too loudly.

I'll try the rest of those instructions and see if they do the trick.  Thanks for the feedback.

---

### Post by Billy McCann on 2007-03-01
FREAKING SWEET!

Now it all works.  As a note, I used the 1.0.14rc**2** driver, lib, and utils, as that's really the latest there is, coming out January 15th, 2007.  You have to modify the directions only a touch.  Replace the "1" with "2" wherever the "1.0.14rc1" happens to appear.  

Time for :guitar:

But my Master Volume in the panel applet still does that funny little dance.  ??

EDIT/RESOLUTION:  This was caused by having the applet mixer applied to the wrong mixer.  I put it on HDA Intel (Alsa) by rick-clicking the icon, selecting preferences, and selecting HDA INTEL (Alsa) in the top drop-down list.  

There is what is cool.  Then there's this -- problem resolution.  It's a feeling all to its own.  I think it's kind of the reason I like Linux.

---

### Post by Roel123 on 2007-03-01
I followed the instructions and also used the latest alsa driver but my problem stays the same. Nice to hear it works for you guys so there is hope that it will work in Feisty :)

I need to do some work on this machine so I'll leave it as it is for now.

Maybe one of you guys can post how you got it to work here [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/87885](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/87885) because I submitted this as a bug.

Thank you

---

### Post by kolach on 2007-03-01
ok, no problem,
I'll post a comment there.

---

### Post by przemek on 2007-03-07
Hello. 
I had the same problem, with my sound, and the same equipment. I did what was written here [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")  in "Manually specify which flavor you are using " and my computer started to "sing". I've used model 3stack. I still has some problems with sound's quality, so I'll have to install new packages from alsa ( r14 ).

---

### Post by Jordan-D on 2007-03-11
The method described here [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) works perfect with me. The drivers i downloaded are 1.0.14rc3 an for the utils 1.0.14rc2. My motherboard is ASUS P5PL2/C and the sound is ADI 1986 on Ubuntu 6.10. I had no sound on the right channel but now i do. Just found that the mixer is not working. I'm gonna play with that later. Oh now its woking just had to select from the preferences Front instead of HeadPhone :). But the ballance is still not working :(

---

### Post by yj09 on 2007-03-26
same with me.. many thing i tried but still not work for me. I using fujitsu c1410.. sound alc262. edgy and now feisty. if any news please update here..

---

### Post by ItsManaged on 2007-12-30
This is an Asus A8Fm series notebook runing gutsy with exaclty the same problem. Followed the instructions on the link above - no joy.

Mine behaves like this with live CD (Ubuntu Gutsy), with the system installed, with all updates (including kernel) (as of 31/12/07) and with the latest ALSA drivers (1.015) as per the link - no joy at all! At a complete loss with what else to try (except a different distro), so I'm just going to get the vista going again on this machine and that is that!

Mind you, my other PC's and the dozens I have converted to Gutsy have worked fine...perhaps it is a hardware thing? I was even considering whether the Vista DRM requirements have been applied to the hardware on this laptop. All long shots.

Happy New Year to you all!

---

### Post by ItsManaged on 2007-12-31
> **ItsManaged said:**
> 

Mind you, my other PC's and the dozens I have converted to Gutsy have worked fine...perhaps it is a hardware thing? I was even considering whether the Vista DRM requirements have been applied to the hardware on this laptop. All long shots.

Happy New Year to you all!

I know it's not DRM'd hardware - PCLINUXOS works just fine.....

---

### Post by ItsManaged on 2007-12-31
Until I touch the volume control! :(

---

### Post by ItsManaged on 2008-01-01
OK, so now I'm some kind of wizard. I went back to a backup of vanilla gutsy install before applying the new alsa modules and other things to get the sound to work. (I'd also tried running OSS) + and then just started installing and uninstalling stuff at random (it never works, but it feels good)). 
Problem with sound dying after I attempt to adjust the volume control was still there in the vanilla - as expected. 
It was obvious to me that either this laptop was going to be running vista or perhaps another OS.
I thought I'd try PCBSD to see if that had the problem too - no it doesn't - sound works great! But wireless support is not quite there for the Intel ABG in this machine - this is a must for the person I'm setting this up for. I booted back into my vanilla gutsy after the PCBSD experience and guess what! Sound works!!! abra cadabra! no hands. Rebooted it a couple of times - all is well! I haven't applied any patches, haven't done anything except run PCBSD on the damm thing. What a fix -can you imagine this as a workaround!!

---

