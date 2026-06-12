---
title: "Can't figure out how to download ubuntu onto external hard drive"
date: 2015-06-21
forum: General Help
---

### Post by michael295 on 2015-06-21
I have windows 7 pro and I'm trying to download ubuntu onto a external hard drive with 500GB. I tried burning the 14.04 ubuntu onto a DVD+R and couldn't get it to burn, so I found an external hard drive but all the videos I've found show me that I need to burn the iso onto a dvd+r first. Can some one PLEASE send me a link to a video or walk me through this. All I want to do is have ubuntu downloaded on my external hard drive so when I start my computer I can either boot from my windows hard drive or my external hard drive so I can use ubuntu. I've literally been trying to do this for over 7 hours. I can't figure out how to burn the iso onto my dvd+r or use daemon tools to mount the image.. I've also tried wubi and I get an error. I really badly want to try ubuntu, I'm starting to think it's impossible. please help!

Is it not possible to download ubuntu onto my external hard drive without having a cd?

---

### Post by VMC on 2015-06-21
Its a two step process. Install the ISO to either a dvd disk or usb flash drive first. Then boot the dvd/flash drive, and install to your external hard drive.
Look at this process on how to install:
[https://builtvisible.com/the-ubuntu-installation-guide/](https://builtvisible.com/the-ubuntu-installation-guide/)

---

### Post by nerdtron on 2015-06-21
What you need:
1 extra USB flash drive (at least 2GB)
Ubuntu ISO
1 external hard drive (your 500GB) - this will be formatted so any data will be lost.
Windows 7
Unetbootin

Steps:
1. Download the Ubuntu ISO.
2. Follow the unetbootin tutorial to make the 2GB flash drive bootable. [https://www.youtube.com/watch?v=l8l6UdrMBIM](https://www.youtube.com/watch?v=l8l6UdrMBIM)
3. Shutdown the computer the disconnect/remove the internal hard drive. This is important so that you will be sure no data will be lost on the windows 7 drive and that all Ubuntu files will be on the external drive.
4. Reboot your computer and set it to boot on the 2GB flash drive to boot ubuntu Live Mode. (test ubuntu)
5. Connect the external drive.
6. On the ubuntu desktop, click the installer and start the installation process. Install ubuntu on the whole external drive.

---

### Post by monkeybrain20122 on 2015-06-22
> **nerdtron said:**
> What you need:

3. Shutdown the computer the disconnect/remove the internal hard drive. This is important so that you will be sure no data will be lost on the windows 7 drive and that all Ubuntu files will be on the external drive.
.

Don't need to if OP choose "something else" when installing from the usb and choose the external drive as the target to install Ubuntu to and intstall the bootloader to be the external drive rather than the internal one in the dropdown (at the bottom of the screen, typically /dev/sdc rather than the default /dev/sda) When I first did this in 10.10 I had more problem following instructions to remove the hard drive than doing this (didn't have a right screw driver handy :))

---

### Post by Mike_Walsh on 2015-06-22
Just a query, but.....is your external hard drive USB 3.0? I have found, by experience, that if I plug it into a USB 2.0 socket, my external hard drive (I have a USB 3.0 500 GB Seagate Expansion HDD) will boot any distro quite happily. 

If, on the other hand, I plug it into a USB 3.0 socket, then, even though I know there's a working OS on the Seagate, it will refuse to boot, and tell me that it can't find it. If you have it plugged into a USB 3.0 socket, just give it a try plugged into a USB 2.0 one.....and see what happens.

There seems to be a big difference between the way that USB 2.0 and USB 3.0 handle data read/writes and transfers; and USB 3.0 doesn't appear to be compatible with GRUB..?

VMC and nerdtron are quite right; for the 'buntus, you do need to burn the .iso to DVD (or install it to USB) first.....and then run this, and perform the installation from there. On the Puppy Linux forums, we are currently experimenting with a way to write .isos directly to a hard drive; but it's still very early days, and 'Puppy' is constructed so differently to just about every other Linux distro out there, that it would definitely never work in Ubuntu.....


Regards,

Mike. ;)

---

### Post by yancek on 2015-06-22
A questions of terminology.  Downloading it to your external drive won't help.  If you had a Linux system on one of your drives with the Grub2 bootloader, you could boot the iso file and install it to a partition.  Since you only have windows, that won't work.  Did you select the option to burn as an image from your DVD burning software?  You need that option for it to be a bootable DVD from which you can then install to your external drive.

---

### Post by dragonfly41 on 2015-06-22
Just for the record there is another option.

You could install VirtualBox in your Windows internal drive.

And then download Ubuntu *.iso and install Ubuntu as a virtual machine inside Windows.

Then after becoming familiar with Ubuntu VM you might use this as a launchpad to configure your external drive to install Ubuntu.

Much depends on your workflow and amount of RAM / space you have since Ubuntu would then be running as VM on Windows.

I assume you've first checked that your BIOS allows USB external drive booting?

---

### Post by sudodus on 2015-06-22
@ [michael295]("http://ubuntuforums.org/member.php?u=1988927"),

There are many tips already, and I will add yet another one. But I will also try to bring some clarity to the situation.

An external drive (USB 2, USB 3 or eSATA) is a mass storage device, just like an internal drive (hard disk drive or solid state drive). It means that you can use it in the same way unless the hardware or software that should communicate has problems (maybe because some part is not quite according to the standard specification). USB 2 is slow, but works. I boot from an SSD connected via USB 3 when I test new versions of Lubuntu and ToriOS. It is almost as fast as an internal drive.

Finally, it is possible to ***boot with the 'grub and iso' method from any drive, internal or external***. In other words, to boot from an ISO file as is. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2259682"]
One pendrive for all PC (Intel/AMD) computers[/URL]

particularly [posts #6,7,8]("http://ubuntuforums.org/showthread.php?t=2259682&p=13300523#post13300523").

-o-

So you can have such a 'grub-n-iso' system near the head end of the external drive, and have a data partition to store your data behind it. If you want to access data from Windows, you might want to make the first partition larger.

But ***maybe what you are aiming at is an installed system in the external drive***, with or without a data partition with access from Windows. I think Windows still needs the data partition to be the first one on the USB drive in order to access it. But that is no problem for Ubuntu. You can make the rest of the drive an extended partition, and install Ubuntu into the drive space in the extended partition. And that can be done automatically or manually. I prefer to know what I'm doing, so I use the manual method, ***Something else*** at the partitioning window of the installer. Remember to select where to install the bootloader (scroll down to the bottom of the partitioning window).

The automatic methods install the bootloader into the first mass storage device which is normally the internal drive. You may or may not want that to happen.

---

### Post by sudodus on 2015-06-22
Hi Mike :-)

> **Mike_Walsh said:**
> Just a query, but.....is your external hard drive USB 3.0? I have found, by experience, that if I plug it into a USB 2.0 socket, my external hard drive (I have a USB 3.0 500 GB Seagate Expansion HDD) will boot any distro quite happily. 

If, on the other hand, I plug it into a USB 3.0 socket, then, even though I know there's a working OS on the Seagate, it will refuse to boot, and tell me that it can't find it. If you have it plugged into a USB 3.0 socket, just give it a try plugged into a USB 2.0 one.....and see what happens.

It works for me. I have an AKASA USB 3 and eSATA box for my SSD, and it boots and runs via USB2, USB3 and eSATA. I use what is the fastest connection.
> 
There seems to be a big difference between the way that USB 2.0 and USB 3.0 handle data read/writes and transfers; and USB 3.0 doesn't appear to be compatible with GRUB..?

I think you have problems with the electronics or some firmware. I have also found that some middle-aged HP computers want the **boot flag** (on the partition to boot), which should not be necessary to boot via grub and USB.
> 
VMC and nerdtron are quite right; for the 'buntus, you do need to burn the .iso to DVD (or install it to USB) first.....and then run this, and perform the installation from there. On the Puppy Linux forums, we are currently experimenting with a way to write .isos directly to a hard drive; but it's still very early days, and 'Puppy' is constructed so differently to just about every other Linux distro out there, that it would definitely never work in Ubuntu.....

Regards,

Mike. ;)

Have a look at this link, [Build your own single boot or multiboot pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682&p=13302278#post13302278") 

Anyway, good luck with the work at Puppy Linux to write iso files directly to a hard drive (and let us know more about it) :-)

---

### Post by Mike_Walsh on 2015-06-22
> **sudodus said:**
> Hi Mike :-)

Have a look at this link, [Build your own single boot or multiboot pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682&p=13302278#post13302278") 

Anyway, good luck with the work at Puppy Linux to write iso files directly to a hard drive (and let us know more about it) :-)

Hi, sudodus.

Hmm. Sounds interesting. In fact, it sounds very similar to what one of our Puppy experts has created a thread about....ISObooter. Have a look at this, if you're interested:-

[http://murga-linux.com/puppy/viewtopic.php?search_id=1824914064&t=67235](http://murga-linux.com/puppy/viewtopic.php?search_id=1824914064&t=67235)

With regard to my Seagate, well.....it's exactly as I said. I've got an install of Zorin OS on it, which I put on a few months ago; interestingly enough, I did **that **with one of your favourites.... MultiBoot.

If I plug it to a 2.0 socket, it boots quite happily. With having a couple of Puppy 'frugals' also on sda, I nowadays use Grub4DOS, rather than GRUB2.....I believe it's what's known as Legacy Grub? Anyway, it works nicely. 

But if I plug it to a 3.0 socket, it just won't boot; insists there's nothing there, and I get all the usual.....kernel panic, not syncing, bad superblock; you name it, up it comes. You're probably right; it's quite likely a firmware incompatibility. The HDD's relatively new, the PC's over 10 yrs old. And before you say 'How can you have USB 3.0 on something that old?', I have a USB 3.0 adapter card which plugs into my single PCI-e x 16 slot, since I don't use a discrete graphics card; I make do with the onboard ATI Radeon graphics chip.....works for me.

I guess that's where the hardware incompatibility is, to be honest. I've found quite a few reports on the 'net that suggest many people have found OS booting doesn't work through these adapter cards. But I mainly fitted the card to speed up large-scale data transfers to/from the Seagate; and it does** exactly** what it's supposed to. So on the rare occasions I use Zorin, I just plug it into a different socket...

I can live with it!

As far as the experimental stuff on the Puppy forums goes; yes, I'll keep you informed. It **is **weighted rather heavily in favour of using Puppy's somewhat unique file-system, so.....I don't know whether it **could **be adapted to Ubuntu. Mind you, you wouldn't believe some of the ideas many of our members come up with... Real eye-openers. They're an imaginative bunch.....and I'm glad I belong to **both** forums.


Regards,

Mike. :)

---

### Post by sudodus on 2015-06-22
Booting with grub-n-iso is an established method. What is new with the method I linked to here is that it works in (almost) all computers from old laptops with Pentium M that need forcepae to new computers that run in UEFI mode. With a casper-rw partition there will be persistence, and it it a handy way to bring an own computing environment in the pocket, and just borrow a computer, when you are away.

I have also made a small script for iso-testing that helps updating the daily isofiles incrementally with rsync. rsync is better than zsync on a slow pendrive. There is no need to make a detour via another drive and an extra copying/cloning/flashing/installing operation.

But Puppy extends even further to really old computers, and makes a computer with Pentium M quite fast and responsive. So I see the need for Puppy and also for convenient ways to 'install' it.

---

