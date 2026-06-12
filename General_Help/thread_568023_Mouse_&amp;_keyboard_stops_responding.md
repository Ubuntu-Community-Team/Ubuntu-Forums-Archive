---
title: "Mouse &amp; keyboard stops responding"
date: 2007-10-05
forum: General Help
---

### Post by Asnem on 2007-10-05
Since the release of Vista, I have been wanting to switch to Linux, like many others.  I had an Athlon 64 X2 system, Asus A8N32-SLI motherboard, 2 GB RAM, ATI Radeon X1900XT, and had freezing issues on the Live CD as well as after install (which I had to do with the alternate CD since the Live CD froze too much).  I finally gave up and bought a new system.

The new system is Intel Q6600 processor, Asus P5K-E motherboard, 2 GB RAM, same video card.

I am having the exact same issues after installing 7.04.  I did a completely clean install.

The symptoms are this.  When I first boot up, things work for a few seconds, then random objects in the gui stop responding to mouse clicks and keyboard input.  The mouse pointer still moves, and sometimes I can click on some things in the current window (like scroll bars) but I can't move or resize the window or click on buttons.  The Gnome menus don't work either.  Sometimes limited keyboard functionality works, like pressing ALT+c to press a close button.  Sometimes if I left and right click all over the place a bunch of times, it will snap out of it briefly.. maybe long enough to click a button.

I don't think it is my install CD, since I have tried 2 Live CDs, and it happens when I install from alternate also.  I have run memtest (no errors - system is brand new).  I am a semi-novice when it comes to Linux, but not a total newb (I had to get around bugs with ATI drivers using recovery console to download updates, before I could even boot into X.  I did enough troubleshooting on my own to find this, which fixed that problem [http://www.mikesplanet.net/2007/04/installing-ubuntu-704-ati-x-cards/]("http://www.mikesplanet.net/2007/04/installing-ubuntu-704-ati-x-cards/"))

I don't think it's hardware either.  On the AMD system, Windows XP would run stable without a reboot for weeks at a time...

There's a similar problem here, but their suggestions didn't work :
[https://answers.launchpad.net/ubuntu/+question/6294]("https://answers.launchpad.net/ubuntu/+question/6294")

There are several other threads with similar issues, but no definite solutions.  I have tried all of the suggestions I have found...

Here's a monster thread about similar issues : [http://ubuntuforums.org/showthread.php?t=412125]("http://ubuntuforums.org/showthread.php?t=412125")

Lots of people on there have gone back to XP or Vista and are waiting until a fix is found.  That's where I'm headed unless someone can come up with a fix.

Any help would be appreciated.  

Thanks

---

### Post by Soybean on 2007-10-05
So... that's two pretty different systems with the exact same problems? 

I see two likely culprits:
1) Some sort of "video card problem." Could be hardware, could be something further with the drivers... but it sounds like the video card is the main thing the two systems have in common, right? To troubleshoot this, I recommend disabling desktop effects, compiz, or beryl, if you're using any of those things. If that fixes your problem, then you can proceed to narrow it down further. If you aren't running any of those, or it doesn't help, I'd try switching to generic VESA drivers. This will not make for a pleasant user experience... it's just a test. See if you still get your lock-ups with the generic drivers. If not, then again... you can narrow it down further from there.

2) Those are both new-ish ASUS motherboards. Could be they share some component that is poorly supported in Linux. Typically, poorly-supported motherboard components are related to power management. So, to troubleshoot this, I'd try changing your kernel boot options: remove "quiet" and "splash", and add "irqpoll" and "acpi=off". You can alter the boot options by editing /boot/grub/menu.lst or by pressing 'e' at the Grub menu when booting. I recommend the latter method for testing, since it's more immediate.


Also, another good general technique is poking around in your log files, in /var/log/, and looking for errors or warnings. Unfortunately, I'm not very good at this, so I just start opening files at random looking for anything that seems weird. Sometimes it doesn't go very well (some of those files aren't even human-readable), but it's pretty common for big problems like this to leave clear traces in the logs.

---

### Post by Asnem on 2007-10-05
Thanks for the reply.  I'm not running anything fancy like Compiz or Beryl.  It's strictly a default install.  It even happens on the Live CD.

The A8N32-SLI is sort of an old board (Socket 939)...  maybe "relatively" new though..  the video card is the only common component; I would consider buying something else if that's the problem.  A new video card will be cheaper than a Vista license :-)

I've already tried some other recommended boot options.  I will try these as well and report back my findings..  I'm not sure there are any Asus-specific things on here; it's using the Intel P35 chipset and the BIOS is pretty generic.

There are a LOT of people having a similar issue, even in 7.10; I'm surprised the cause hasn't been found.

Thanks

---

### Post by Asnem on 2007-10-05
Here's another person having the same issue : [https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/109740]("https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/109740")


I tried switching to VESA, but I couldn't get my LCD monitor to work.  I only allowed VESA modes, but my refresh frequencies must have been off.  I put back the ATI driver through recovery console, and it was stable for a few minutes, until I opened Firefox.  That may have been a coincidence.

I'm going to try some different BIOS settings.  Most people seem to be triangulating on something to do with either multi-core CPU's or CPU power saving features.

---

### Post by strabes on 2007-10-05
If you can, return the ATI video card and exchange it for an nvidia. ATI's linux drivers are unacceptable. They give terrible 3d performance and don't support beryl/compiz with AIGLX.

---

### Post by Asnem on 2007-10-06
I just downloaded and booted the 7.10 Beta Live CD.  I am getting the same symptoms, and it appears to be using the Vesa driver.  

I may be getting an Nvidia card to see if that helps.  I don't need super high end 3-D graphics.  Mid-range would be fine.  Any suggestions?

Is it better to go with a previous generation card, or is the 8xxx series OK?

I forgot to mention earlier, one of the strange symptoms I have, that even happens on the Live CD, is that I can't click on Desktop icons.  I can highlight them, though.  When I try to click on Desktop icons, it's as if they are part of the wallpaper.  They don't respond at all.

---

### Post by Asnem on 2007-10-07
I just replaced my video card with Nvidia (Geforce 7100 GS) and DVD-RW drive with a new one (Pioneer).  There's virtually nothing left from my old system, but I still have the same symptoms.

---

### Post by idomagic on 2007-10-20
I'm having a similiar problem on my abit IP35 pro (p35 based) system.

After some random amount of time after boot both keyboard and mouse (connected to ps/2) stops responding entirely, but everything else is running fine. No keys at all are responding, not ctrl-alt-backspace, not caps/num/etc, mouse pointer is not moving, suspending/hibernating the computer does not help, only a full reboot solves the issue.

If I switch the mouse to usb it's working normally and I can check logs etc, but I've found no sign of anything going wrong in there. It even detects when I disconnect my mouse from the ps/2 port: "psmouse.c: Explorer Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away."
"psmouse.c: resync failed, issuing reconnect request"

I'm using a kvm which is working perfectly with my two other ubuntu systems, so I'm guessing this is a driver issue.

Specs on my problem system:
Abit IP35 pro
q6600
8800gtx (using repo nvidia-glx with twinview)
2gb ram
ubuntu 7.10, flavour does not matter, the issue is present in k/xubuntu as well.

One of my other systems that's working perfectly has a nforce2 motherboard with 7600gt, also using twinview although not nvidia drivers from repo.

---

### Post by idomagic on 2007-10-20
When fiddling around with an onscreen keyboard suddenly the keyboard came to life again.. It's not reinitializing my mouse on the ps/2 port though, usb mouse still works.

---

### Post by Asnem on 2007-10-20
Just tried 7.10, same issues.  I can't click on the desktop icons.  Other user interface elements randomly don't work...

I have a Quad Core processor.  

I can reproduce this 100% of the time.  How can I get someone to take a serious look at this before I give up and switch to Vista?  I have spent $500 replacing components on my PC trying to get Ubuntu to work!!!

---

### Post by hotani on 2007-10-20
Same problem here. Using a Dell Latitude D600. Never had the problem before gutsy, now I can use the machine for some random amount of time before the mouse becomes unresponsive. It is as if clicks only activate the last thing clicked before the problem started. For example: if the last thing I did was click the pidgin icon to show the buddy list, no matter where I click, that is what responds. ctrl+alt+backspace is the only fix I have found so far.

---

### Post by robinlennox on 2007-10-26
I've been having the same issues. Has anyone managed to sort this issue out?

---

### Post by robotsperm on 2007-10-27
Being a huge Microsoft fanboi, I never thought I would be posting for help here!  But the cube desktop and my recent torrid love affair with Window Vista has caused me to cheat with Gusty.  So this is a great chance to test the public software movement and its ability to quickly react to its users needs.

I have a Lenovo C200 8222FU with Gusty 7.10 newly loaded on it.  Same exact problem everyone seems to be having.  The mouse will act erratic and crash the system occasionally Here are the necessary log files: 

Oct 26 23:49:36 LAPTOP kernel: [ 8780.484000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Oct 26 23:49:36 LAPTOP kernel: [ 8780.484000] psmouse.c: issuing reconnect request
Oct 26 23:49:37 LAPTOP kernel: [ 8781.036000] input: PS/2 Generic Mouse as /class/input/input19
Oct 26 23:49:37 LAPTOP kernel: [ 8781.036000] psmouse.c: Failed to enable mouse on isa0060/serio1

I'm also recieving alot of these messages: 

Oct 26 23:29:37 LAPTOP NetworkManager: <debug> [1193466577.670531] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX0_port_logicaldev_input'). 
Oct 26 23:49:36 LAPTOP NetworkManager: <debug> [1193467776.732219] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX0_port_logicaldev_input'). 

Ok guys, let me know if you have any questions or need anything else from me.  Now I am no stranger to systems administration, but I ask that you don't post technical requests that an 'average user' wouldn't understand or be able to do.  This is my first test of Linux for personal daily use, and I am keeping a close eye on how this issue develops to 'write home about'. 

Good luck!

---

### Post by idomagic on 2007-11-05
Bah, after not having any issues for a few days, suddenly both mouse and keyboard died on me again, but when connecting a usb-mouse the keyboard came back to life.

Getting these errors when it happened:

Nov  5 23:57:58 idoit kernel: [90593.873839] psmouse.c: Explorer Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Nov  5 23:57:59 idoit kernel: [90593.967990] psmouse.c: resync failed, issuing reconnect request

Nov  5 23:57:59 idoit NetworkManager: <debug> [1194303479.279422] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 

Nov  5 23:58:31 idoit NetworkManager: <debug> [1194303511.437593] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 

Nov  5 23:59:55 idoit kernel: [90710.760280] psmouse.c: Explorer Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
Nov  5 23:59:56 idoit kernel: [90711.233937] psmouse.c: resync failed, issuing reconnect request

---

### Post by a4nic8er on 2007-11-16
Kubuntu 7.10 loses keyboard, mouse cursor still moveable but nothing clickable.

This occurs after a time while performing an operation (whether OS is installed or running from live CD) forcing a hard reset. Does not happen if left idle after booting, but will happen after a time while performing an operation after this. Can happen during install if machine has been left idle from live CD boot. Occured while adjusting time, while setting screensaver, while reading logs, while checking partitions, and during install. 

System:
Asus A7V mobo
AMD Thunderbird 1100
1gb PC133 RAM
Abit Radeon 9600XT 256MB
PS2 mouse and keyboard.

Windows 98SE, Windows XP, SUSE Linux 10.0, have all been installed and run on this system without any problem.

Gutsy Gibbon - "Drops it's guts regularly!" ;)

---

### Post by Asnem on 2007-11-18
I think I have my system fixed.  I replaced my Asus motherboard with Gigabyte and it didn't help.  I tried installing Vista and had similar issues!  Then I found that the -5v line on my power supply was bad, so I replaced that, but still have the problem.

I replaced my mouse and keyboard, and now haven't had the problem since.  I think I might have had a bad mouse that was fouling up the X.org.  It worked fine in WIndows, however.

If anyone is still having problems, try swapping your mouse and keyboard, and post your results here.

---

### Post by Melcar on 2007-12-06
I'm experiencing a similar problem with my main system.

Opteron 165
2GB DDR500 RAM
DFI NF4 MOBO
X1950XT

I happens rather random, but I can never keep my system up for more than a few hours without this problem eventually rendering the whole desktop useless (only a reboot fixes it).  Basically, the keyboard will "die" all of a sudden (it stops responding), and while I can still move the mouse pointer, clicking stuff produces no effect and programs would stop responding (even ndiswrapper "crashes").  This has been happening on several Ubuntu 7.10 and OpenSuse 10.3 installs, so it must either be my hardware or a problem with the distros themselves (both versions are 64bit).  At first I thought it was the video card and/or video drivers, but the problem happens regardless of whether I'm using Vesa or fglrx.  I'm going to try 32bit versions now and see if the same problems are there.  Windows (XP 32bit) works fine by the way.

---

### Post by kolesar on 2007-12-20
Same happens with me. IBM ThinkCentre 8183 21G with 2.6 GHz Northwood, 512 MB DDR RAM. Mouse moves, Firefox page animates ads, time is updated on desktop. Mouse clicks and keypresses are not processed.

---

### Post by Ralphie on 2007-12-20
I have just started to get this problem, it has happened twice now. 
the only recent change on my system was a new mouse after my old one died. the new one is a cheapo microsoft one that came with a computer a while back. 

it has acted erratically (unlike my old one), as someone has described in this thread, and now i am getting this problem with the keyboard and mouse buttons going out except i can still move the mouse, forcing me to hard reset.

I think i am going to buy a better mouse soon. we will see if this changes anything.

---

### Post by Ralphie on 2007-12-22
well i just got a new mouse, logitech LX5, and it was still happening.

I changed my keyboard out with a new one that uses the USB instead, and the problem still has not been fixed.

i dont know if the two problems are related or not, but do people with this issue also sometimes have an issue with ubuntu hanging while loading up? i found that certain usb devices, if plugged in while starting this new system i just built, will cause it to freeze while starting up, and my only option then, like now is to hard reset.

---

### Post by Ux64 on 2008-06-08
> **robinlennox said:**
> I've been having the same issues. Has anyone managed to sort this issue out?

Nope. I'm using Hardy Heron and still suffering from same problem.

[http://ubuntuforums.org/showthread.php?t=814622](http://ubuntuforums.org/showthread.php?t=814622)

---

### Post by tgyorgyi on 2008-06-14
I have an FSC Amilo laptop, keyboard and touchpad started behaving like those described by others. None of the suggestions helped. I have XP running on the same machine on a different partition for two years and on, and when I switch to XP, keyboard and touchpad are working fine, never experienced anything like this there.

---

### Post by Ux64 on 2008-06-15
> **Ralphie said:**
> well i just got a new mouse, logitech LX5, and it was still happening.
I changed my keyboard out with a new one that uses the USB instead, and the problem still has not been fixed.


I knew from the symptoms that it had nothing to do with physical hardware like mouse or keyboard. It might have something indirect to do with motherboard, but most propably it's clear software bug.

---

### Post by Ux64 on 2008-06-18
Tons of new updates loaded. Yet no help. ;( Gotta hope that they'll fix this problem at some point too.

 - Thanks

---

