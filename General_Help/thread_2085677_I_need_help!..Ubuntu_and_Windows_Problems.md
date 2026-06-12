---
title: "I need help!..Ubuntu and Windows Problems"
date: 2012-11-18
forum: General Help
---

### Post by Glorygamer on 2012-11-18
So..my windows computer got the BSOD and so I decided to switch to ubuntu (12.10) and I installed it via USB so my intention was to install ubuntu and then delete windows 7 and re-install windows 7..I downloaded a ISO file of the Windows 7 Installation Disc (32-bit and Home Premium) and put it on another USB..so when I went to change the boot selection..it wouldn't let my into my BIOS or boot manager..it took me straight to GRUB..I then got VirtualBox to try and install windows through that..when I got to the install part it said two things..one was "Disk 0 Partition 1 Unallocated Space 100MB" and number two was "Disk 0 Partition 1 Reserved" and was 25GB which I assumed had ubuntu on it (since I gave Ubuntu 30GB when I was installing it)..I couldn't install it on the first option because it was 100MB and I don't know why it wouldn't show any other drives..and I didn't install it on number two because I thought it had ubuntu on it..so I went to OS-Uninstaller and made it uninstall windows 7 and when it completed..I formatted the C drive (it was ntfs and said WINDOWS so that's the one I deleted) but not my D drive which said Data..but when I went back to my VirtualBox it still said the same two options and I was really confused..so now ubuntu is really slow and when I restarted my computer..I can't enter the BIOS,Ubuntu is slow and gets errors starting up but eventually gets into the OS and when it does its slow,I can't start up VirtualBox due to some error and when I start up Gparted (which I used to format/do anything with my drives) it has red exclamation marks besides there name and I can't do anything..please help somehow I just want to completely format my entire computer including ubuntu and get access to the BIOS so I can change the boot order and install windows 7 again..somebody help please :(

---

### Post by AlanQ on 2012-11-18
Glorygamer, did you take a breath at any point in all that? :)

> ..it wouldn't let my into my BIOS or boot manager..it took me straight to GRUB..

Are you sure you're pressing the right key to get into your BIOS?
In my experience its usually either <Delete>, <Esc> or <F2>.
No OS can prevent you from getting into your BIOS. It's the BIOS that calls GRUB, so the BIOS is in control first.

> I then got VirtualBox to try and install windows through that..when I got to the install part it said two things..

"it said" -- what is 'it'?

I think you may be confused with what VirtualBox does. VB creates Virtual Disks which are _files_ *within* your filesystem *on* your hard drive.

Before doing any more, are there any files that you need to back up from Windows?
If you boot into Ubuntu from the USB device you can use that to mount your hard disk's Windows partitions and copy files to another device.

If I understand correctly, you want Ubuntu as your main Operating System and Windows as either dual-boot or in a Virtual Disk to be accessed using Virtualbox. Yes?

Having read the other things you say, I would recommend using Virtualbox. One big advantage is that you can clone Virtual Disks. This means you can work on a clone when making major changes to Windows. If it all goes wrong, you've still got the original without having to re-install.

---

### Post by Glorygamer on 2012-11-18
I breathe all the time :) even now... It's .just the frustration of getting this is thing to work! :(

Yes,I'm sure I'm pressing the right key to enter the BIOS, When my computer starts up it says "Press F2 to enter Setup Utility" or "Press F12 for boot manager". No matter which one i press it just goes to a black screen and then a few seconds later up come GRUB asking me to boot Ubuntu or Windows (I can only boot Ubuntu because Windows won't even boot up because of the boot screen)

When in VirtualBox trying to install Windows it gave me two options of which Drive or "Disk" as they put it,I could install Windows on. "Disk 0 Partition 1" which was 100MB and "Disk 0 Partition 2" which was 25.0GB and had 24.9GB which I assumed was Ubuntu since I give 30.0GB to Ubuntu whenever I was installing Ubuntu off the USB

And finally,No,My intention was to:

Install Ubuntu
Delete Windows 7
Re-install Windows 7
(I don't mind keeping Ubuntu but I want Windows 7 as my main OS)

---

### Post by AlanQ on 2012-11-18
> I breathe all the time :) even now... It's .just the frustration of getting this is thing to work! :(

:) I know the feeling.

> Yes,I'm sure I'm pressing the right key to enter the BIOS, When my computer starts up it says "Press F2 to enter Setup Utility" or "Press F12 for boot manager". No matter which one i press it just goes to a black screen and then a few seconds later up come GRUB asking me to boot Ubuntu or Windows (I can only boot Ubuntu because Windows won't even boot up because of the boot screen)

Hmm...
Try pressing <F2> repeatedly from the moment you start up the computer.
If that doesn't do it, do the same with <Esc> and <Delete> -- just in case the message is wrong.
Failing that, try a web search on the make/model of your machine with "BIOS" and/or "F2".

> When in VirtualBox trying to install Windows it gave me two options of which Drive or "Disk" as they put it,I could install Windows on. "Disk 0 Partition 1" which was 100MB and "Disk 0 Partition 2" which was 25.0GB and had 24.9GB which I assumed was Ubuntu since I give 30.0GB to Ubuntu whenever I was installing Ubuntu off the USB

I'm still confused by this but no matter because what you actually want to do is...

> And finally,No,My intention was to:

Install Ubuntu
Delete Windows 7
Re-install Windows 7
(I don't mind keeping Ubuntu but I want Windows 7 as my main OS)

Boot Ubuntu from the USB device (or a CD/DVD).
Don't install it, just run it from that device.
In the Unity panel on the left, click the top icon (Ubuntu logo), and type disk.
One option should be 'Disk Utility'. Click that. It will allow you do delete all partitions so the disk is 'clean' and ready for a Windows install.
Shutdown Ubuntu. Install Windows. Job done.

---

### Post by gnusci on 2012-11-18
> **Glorygamer said:**
> I breathe all the time :) even now... It's .just the frustration of getting this is thing to work! :(

Yes,I'm sure I'm pressing the right key to enter the BIOS, When my computer starts up it says "Press F2 to enter Setup Utility" or "Press F12 for boot manager". No matter which one i press it just goes to a black screen and then a few seconds later up come GRUB asking me to boot Ubuntu or Windows (I can only boot Ubuntu because Windows won't even boot up because of the boot screen)

When in VirtualBox trying to install Windows it gave me two options of which Drive or "Disk" as they put it,I could install Windows on. "Disk 0 Partition 1" which was 100MB and "Disk 0 Partition 2" which was 25.0GB and had 24.9GB which I assumed was Ubuntu since I give 30.0GB to Ubuntu whenever I was installing Ubuntu off the USB

And finally,No,My intention was to:

Install Ubuntu
Delete Windows 7
Re-install Windows 7
(I don't mind keeping Ubuntu but I want Windows 7 as my main OS)

It looks like you are having problems with your hardware and there is nothing to do with Ubuntu, that correctly run in several millions of PCs nowadays. You may get better help in other forums I guess, since you problems are not Ubuntu related, anyway some people can try to help you but they cannot fix your hardware issues, try hard resetting the BIOS and use a LiveCD to fix your HD.

---

### Post by Glorygamer on 2012-11-18
Okay in the last part you said there about booting from the USB..it worked and now I'm back in Ubuntu but its running off the USB instead if the Hard Disk..but when I search for 'Disk Utility' it's not there?..all I get are 'Disk Usage Analyzer'
'Startup Disk Creator'
'Disks'
And then the option to install ubuntu

So I went into 'Disks' and my 500GB hard drive came up..it wouldn't let me format it so I just deleted the partitions one by one and then it said '500GB free space'..I then shut down ubuntu and removed the USB which had Ubuntu on it and inserted the USB which had my Windows Installation on..but when I went to set up the BIOS it wouldn't let me..it did the same thing again except this time it said...

No bootable partition
grubrescue<

So I shut off the computer and restarted it and it still wot let me into the BIOS :(

---

### Post by AlanQ on 2012-11-18
Most BIOS are set up by default to boot from the CD/DVD drive before the first hard disk.

Can you burn Windows to a CD/DVD and try to boot from that?

If that doesn't work the you'll need help with the hardware to get into the BIOS.

There might be an option to move a jumper on the motherboard to reset the BIOS. But you need to know what you're doing!

Try searching/posting on a hardware forum...

Good luck.

---

### Post by Glorygamer on 2012-11-19
I'm able to get back into the BIOS after alot of fiddling about :D

My new problem is that I when I go to install windows off the USB it then shows me this error

BOOTMGR is missing
Press Ctl+Alt+Del to Restart

:(

---

### Post by AlanQ on 2012-11-19
You'll need a Windows forum now...

---

### Post by Mark Phelps on 2012-11-19
> **Glorygamer said:**
> I'm able to get back into the BIOS after alot of fiddling about :D

My new problem is that I when I go to install windows off the USB it then shows me this error

BOOTMGR is missing
Press Ctl+Alt+Del to Restart

:(

THAT means your PC is trying to boot from a Windows boot loader -- and can't find any.  Two possibilities: (1) USB was not made correctly (and lacks the boot loader), or (2) the PC is STILL trying to boot from the hard drive.

My suggestion is to check a Windows 7 forums (sevenforums.com) as they have tutorials on how to make the install USB and how to do installations.

---

