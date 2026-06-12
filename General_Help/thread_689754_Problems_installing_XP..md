---
title: "Problems installing XP."
date: 2008-02-06
forum: General Help
---

### Post by Hurrdurr on 2008-02-06
I have been using Ubuntu for many months now with minimal problems thankfully, but unfortunately I am now needing to use windows XP. I have the setup cd, but it will not start when I boot the computer or do anything if I try installing after running the setup in wine. (Error immediately after starting.) How would I go about installing/formatting if needed? Having to reinstall Ubuntu is not a problem later on I suppose.

---

### Post by pointone on 2008-02-06
You need to make sure the system is configured to attempt to boot from CD before trying to boot from the hard drive. This is accomplished either by editing settings in the BIOS, or available by pressing Esc, F12, or some other key during boot for a one-time boot menu.

---

### Post by upthelum on 2008-02-06
Well if you don't mind wiping everything just backup then boot the windows disc, delete the partition, set up winblows then boot the ubuntu disc which will set up grub for dual-boot. That way you can keep your linux and have 2 OS's if needed. Unless anyone has another suggestion.

---

### Post by Hurrdurr on 2008-02-06
Unfortunately I have no luck that way, hopeless with computers it seems. How can I go about formatting the hard drive, is there a command? I would search, but I'd rather have confirmation please as I'm worried I'm going to mess up badly somehow.

---

### Post by upthelum on 2008-02-06
Like pointone says, you have to set your machine to boot from cd so when you switch it on you'll have to press f12, f8 or some other key to get into the boot menu and check.

---

### Post by Hurrdurr on 2008-02-06
From what I can see it should boot from cd first, I'm even more puzzled now.

---

### Post by upthelum on 2008-02-06
> **Hurrdurr said:**
> From what I can see it should boot from cd first, I'm even more puzzled now.

If it's set to boot from disc and the disc won't boot then consider there could be a problem with the disc.

---

### Post by Hurrdurr on 2008-02-06
Okay, I'll stop for now. Cheers mate.

---

### Post by upthelum on 2008-02-06
> **Hurrdurr said:**
> Okay, I'll stop for now. Cheers mate.

Glad to help, only wish had sorted the problem, later...

---

### Post by astrotech226 on 2008-02-06
Could you try to install XP inside Virtualbox or VMWare?  That way, you don't lose your Ubuntu install and can run XP whenever you want.  If you've never tried it, it's pretty amazing.  Rebooting the XP virtual machine takes like seconds compared to the minutes a regular PC would.

---

### Post by RedPandaFox on 2008-02-06
The problem is not the disk or anything, it is that windows dose not like being second to anything, it likes to have a wiped PC, If your backing up, back up to a disk, wipe ubuntu completely and just leave it as raw memory, then install XP, it should boot from disk if all other partitions are gone.
This is what happened to me. Once all the partitions were gone and no trace of other OS's (well atleast readable to XP) the XP disk booted alright.

---

### Post by Hurrdurr on 2008-02-06
> **RedPandaFox said:**
> The problem is not the disk or anything, it is that windows dose not like being second to anything, it likes to have a wiped PC, If your backing up, back up to a disk, wipe ubuntu completely and just leave it as raw memory, then install XP, it should boot from disk if all other partitions are gone.
This is what happened to me. Once all the partitions were gone and no trace of other OS's (well atleast readable to XP) the XP disk booted alright.

How would I go about wiping everything then please? I can't find anything that looks like it would do it on the menu...

---

### Post by astrotech226 on 2008-02-06
> **RedPandaFox said:**
> The problem is not the disk or anything, it is that windows dose not like being second to anything, it likes to have a wiped PC, If your backing up, back up to a disk, wipe ubuntu completely and just leave it as raw memory, then install XP, it should boot from disk if all other partitions are gone.
This is what happened to me. Once all the partitions were gone and no trace of other OS's (well atleast readable to XP) the XP disk booted alright.

Ah....  You must not have been exposed to virtual machines yet!  It is really cool if you haven't tried it.  Windows won't have any idea that there are other partitions, Linux, etc...

What happens is that the VM software will set aside so many resources for your Windows installation.  So let's assume 8G of drive space and 256M RAM.  You go into the VM console and you start your newly created virtual machine.

This is where it gets hard to wrap your head around it until you've done it a few times.  Your Windows installation is happening in it's own little world.  As far as it's concerned, it is THE ONLY OS on the computer.

A cool feature is the ability to pause the virtual machine.  Here's a scenario.  You boot Linux and and do some things.  You need to see something in IE7 and need to do it from XP.  Start your virtual machine.  A window opens in Linux and you watch Windows XP boot.  And this is not wine running, it's windows!

You do what you need to in IE7.  Now, you can pause the virtual machine.  It saves it's state sort of like hibernate on a laptop.  You can reboot your PC a hundred times, come back to the virtual machine and start it back up.  Your IE7 window is exactly where it it was before.

I've used both VMWare and VirtualBox.  I've had better luck with VMWare, but you have to register to get the key to use it, even though it's free.

Does this sound like it would help your situation any?

---

### Post by RedPandaFox on 2008-02-07
From what I can gather, yeah a VM will be good for if you need it occasinaly and want to have a PC dedicated to Ubuntu with nothing windows except the VM.
But what some people prefer to do is just have it duel boot. I have 2 windows boots on one hard drive and 3 Linux (Ubuntu/PClinuxOS/Zenwalk) On my other hard drive. I prefer it this way so if I need to do something like messenger, I might prefer it on windows, or browsing, or games etc on diffrent OS's. 
But thats a personal preferance

---

### Post by jamyskis on 2008-02-07
Hurrdurr - I can understand your situation, but coming into a dedicated Ubuntu forum and asking for help on switching back to Windows is not a very good idea [-X

As others have suggested, if you need WinXP for certain tasks (not games) then I would recommend VirtualBox. You can use QEMU but it can be fairly difficult to configure, and you could use Vmware but it costs a fair bit of money. I run WinXP for various needs under VirtualBox and I have absolutely no problems with it. You can even set it up so that Windows programs in VirtualBox blend in with the Ubuntu environment!

You can get Ubuntu binaries from [http://virtualbox.org/wiki/Downloads](http://virtualbox.org/wiki/Downloads)

Dual-booting is also a possibility if you need a Windows gaming partition, but do the partitioning within Ubuntu, as Windows doesn't play nice with other OS's.

HTH
J

---

