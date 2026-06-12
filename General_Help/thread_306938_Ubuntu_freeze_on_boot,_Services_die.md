---
title: "Ubuntu freeze on boot, Services die"
date: 2006-11-25
forum: General Help
---

### Post by vakont on 2006-11-25
Hello there my friends!
I met Ubuntu a few days ago and I loved it so much that I went out to buy a laptop for it!... Everything started normally, until I found out that the live CD just happened (one out of 20 times) to boot up and I was able to install it. After that, every time I try to boot, no matter if it's the hard drive or the Live CD.

It happens once the boot progress bar is about 40% of the total boot. Then it stops for about 2 minutes and goes to a black screen that just says that the fsck has checked the sda1 hard drive and another fsck line below it that says the same thing but no target drive. Both lines present the [OK] sign.

From there on, everything freezes to a dead lock. The same thing happens 19 out of 20 times with the Live CD. And I reinstalled Ubuntu 4 times, so imagine how many efforts had to be made!

The only way I can "escape" the dead-lock is to press CTRL+ALT+DEL (man, I am starting to feel like fighting Microsoft Windows here...) and it unlocks and starts the XServer (Gnome). Only there, no services are present and no changes can be done to the system whatsoever. I can't see my DVD and even the device (scd#) is not present in the /dev folder. Not to mention that both my USB stick and my USB external hard drive are "flying somewhere in Hawai for vacation"! (I mean that they are totally invisible to the system).

It may show all the services disabled, but it shows the level of my battery!

Can please anyone help me with this one? I absolutely adore Ubuntu and I would hate to have to install another distribution (I have Mandriva 2007 Powerpack+, which I don't actually enjoy) and I definitely don't want to consider Windows (I formated the hard drive as soon as I got the laptop out of the box).

My system is a customized version of Clevo's systems:
Clevo M57U
Pentium Core Duo 2.16GHz
2GB RAM DDR2/667MHz
nVidia GeForce 7950, 512MB
120GB SATA Hard Drive
DVD ROM/RAM/RW
1Gbit Ethernet, Wireless & Bluetooth network

I hope I am not forgetting anything of use.


Thanks in advance guys... I desperately need your help!

---

### Post by Tom H on 2006-11-25
I have a Gateway P3 500MHZ with 384Meg ram and 60G HD.  I have burned the 6.1 and 6.1 Alternat at 23 and 4x and both do same thing. Get to sign on screen (sometimes) most of time just a blank screen and then machine freezes.  The ONLY way out of it is shut power off.  It is getting frustrating.  

Tom H

---

### Post by Tom H on 2006-11-25
I just tried to reboot it and before it locked up I kept pressing ctl,alt F1 and got to the text screen and it locked while there and    
I got to see this error "Soft lockup detedted on cpu#0!"  if that helps anybody any ideas would help, thanks.

Tom H

---

### Post by vakont on 2006-11-26
One other thing I noticed is that my laptop's DVD RAM is wrongly setup. I just did another setup and it booted (one of the very rare occasions). I try to open it and I get an error message of an inexistent device. Could this be it? 

Because all options regarding noapic, nolapic, acpi=off etc at boot up, nothing helped... not even close.](*,)

---

### Post by Tom H on 2006-11-26
I tried to reboot from CD I installed from and ran the "rescue broken system" first I was able to do a shell to command line but when I came back to menu it locked up.  So rebooted and did it again and did "reinstall grub loader" and this gave me "exit code 20 error" and I just shut it down.

Tom H

---

### Post by Tom H on 2006-11-28
Since nobody seems to have any answers to this problem is there another version sombody could suggest I download to try?

Tom

---

### Post by Tom H on 2006-12-02
Got it working.  I was able to do things from text screen but not boot (it would freeze) swapped video cards and it is working (I am on 6.1 now.  Now when it was installing it said run (what I wrote down) oem-config-prepare and that would delete the oem user and let me set myself up as regular user but can't get that to work so don' know if I wrote it down wrong or what?  I know I can just set myself up and then switch to that log on but if I don't need the oem user then I would prefer to delete that correctly.  Maybe though ( have not looked) where I add user I may be able to delete it there.

Tom

---

### Post by vakont on 2006-12-03
I managed also to stabilize my Ubuntu Edgy and as I figured out it had mostly to do with my SATA DVD-RW, which doesn't function at all. I am trying to solve through this, but it seems to be a more general problem with some specific SATA protocol DVDs. It's a laptop incompatibility I have spotted [here]("http://ubuntuforums.org/showthread.php?t=299587").

---

### Post by jessecollins on 2006-12-12
I am having the same problem with Edgy.  

Is this about the same spot in the splash screen where the boot process freezes?

[IMG]http://www.jessejcollins.com/files/ubuntu_freeze.JPG[/IMG]

---

### Post by taurus on 2006-12-12
> **jessecollins said:**
> I am having the same problem with Edgy.  

Is this about the same spot in the splash screen where the boot process freezes?

[IMG]http://www.jessejcollins.com/files/ubuntu_freeze.JPG[/IMG]

Hello #7!

If you want to install Edgy on your machine, try using the alternate CD then...

---

