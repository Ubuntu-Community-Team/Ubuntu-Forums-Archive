---
title: "Ubuntu 15.04 64 can't boot to flash UBS stick"
date: 2015-09-21
forum: General Help
---

### Post by AgentZ86 on 2015-09-21
I create usb stick live boot 15.04 64bit with unetbootin as described from the ISO download

I can load one of my older machines the other machine won't boot to flash stick

Specs
AMD FX 8350 8 core with Asrock 990extreme3
16GB ram
GTX 970

This is a USB stick and I can boot to the menu selections
However, neither options to install or to try ubuntu without install will boot.

I know the machine boots to the flash because it worked on another machine and I get the boot menu

try ubuntu gives me black screen and no indication that anything is happening.
install gives a lot of screen readout that looks like mostly errors perhaps, but never does much of anything else nor does it say it's failed, or stopped etc. 

Please advise

---

### Post by oldfred on 2015-09-21
You may need UEFI settings/changes. Or make sure you are not using Asmedia ports.
 Some have issues with Asrock and its asmedia ports

 Sabertooth 990FX: Easy solution to get IOMMU working on mobos with broken BIOSes. 
[http://ubuntuforums.org/showthread.php?t=2254677](http://ubuntuforums.org/showthread.php?t=2254677)
      
 ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)

You will also have to use nomodeset until you install nVidia driver. Do not install nVidia from nVidia with .run file, but from ppa.
 Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[http://ubuntuforums.org/showthread.php?t=2259210](http://ubuntuforums.org/showthread.php?t=2259210)

      
 Nouveau vs. NVIDIA GeForce Linux Performance At The End Of 2014
[http://www.phoronix.com/scan.php?page=article&item=nvidia_nouveau_2014&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_nouveau_2014&num=1)
The GeForce GTX 970/980 new Maxwell GPUs also couldn't be tested since there isn't any hardware acceleration support with Nouveau and that's currently blocked by NVIDIA providing their new signed firmware images. Or only nVidia will work.


 Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
sudo apt-add-repository ppa:graphics-drivers/ppa.

---

### Post by AgentZ86 on 2015-09-21
Yikes, that is a lot of reading to do.

I installed 14.04 on this machine easily no uefi issues. I don't have it enabled in bios anyhow.
I wanted to reinstall fresh 15.04 but ran into this problem including with the creation of the 15.04 flash disk which appeared to need netubootin to create this time as oppose to the startdisk creator.

Thanks I will start reading. 

Back to the drawing board

P.S 
I did have to install my GTX driver but only after upgrading cuda could I get it working.
I didn't consider that a new install would still have this problem with GTX 970 / 980's

---

### Post by AgentZ86 on 2015-09-21
> **oldfred said:**
> You may need UEFI settings/changes. Or make sure you are not using Asmedia ports.
 Some have issues with Asrock and its asmedia ports

 Sabertooth 990FX: Easy solution to get IOMMU working on mobos with broken BIOSes. 
[http://ubuntuforums.org/showthread.php?t=2254677](http://ubuntuforums.org/showthread.php?t=2254677)
      
 ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)

You will also have to use nomodeset until you install nVidia driver. Do not install nVidia from nVidia with .run file, but from ppa.
 Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[http://ubuntuforums.org/showthread.php?t=2259210](http://ubuntuforums.org/showthread.php?t=2259210)

      
 Nouveau vs. NVIDIA GeForce Linux Performance At The End Of 2014
[http://www.phoronix.com/scan.php?page=article&item=nvidia_nouveau_2014&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_nouveau_2014&num=1)
The GeForce GTX 970/980 new Maxwell GPUs also couldn't be tested since there isn't any hardware acceleration support with Nouveau and that's currently blocked by NVIDIA providing their new signed firmware images. Or only nVidia will work.


 Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
sudo apt-add-repository ppa:graphics-drivers/ppa.

The threads for nomodeset for GTX970 are said not to have worked per the thread.
It does not appear that any live CD or flash can boot to the GTX970 except to jump through major hoops and install first, then do something with ppa and other stuff.

I wondered if it would be possible to boot the flash disk on another machine that has an older nvidia card that also uses the proprietary drivers such as 340 etc.  Are these the same drivers that include a bunch of drivers including the GTX970 ?

Can an install of this driver create a condition that might allow the other machine with GTX970 to boot from the flash ?
Guess I'll find out

---

### Post by sudodus on 2015-09-21
Have you tried to boot from the pendrive with the boot option **nomodeset**. It is described for a boot in BIOS at the following link:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

In UEFI mode you boot into grub2 also from the pendrive (similar to the installed system), so you need instructions how add nomodeset in grub2.

Press the **E** key and after that move the cursor down to the line starting with **linux**. Move the cursor to the end of that line and add the text nomodeset (separated by a space) at the end of the line. Continue booting with the hotkey combination

***ctrl  + x***

For the installed system

Look for **GRUB_CMDLINE_LINUX** in the following link

[https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

[code]sudo nano /etc/default/grub[code]

Run sudo update grub after editing the file with that line

---

### Post by AgentZ86 on 2015-09-21
> **sudodus said:**
> Have you tried to boot from the pendrive with the boot option **nomodeset**. It is described for a boot in BIOS at the following link:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)



I would have loved to hit F4 and try different modes. 
I can't seem to figure out exactly what to put on the command line once I hit tab

I don't seem to have any of these options prior to any welcome screen. 
With the unetbootin creation of the live pen drive the boot options appear to be different. 
There is a bug in the startdisk creater that doesn't allow a pen drive creation that will boot properly so they recommend unetbootin which now changes the entire boot option selection including the F1-F7 options

I don't know what to do now. It seems ubuntu 15.04 just can't work on newer hardware without jumping through a lot of hoops. I mean a lot



Thanks

---

### Post by AgentZ86 on 2015-09-21
Ok, I can hit TAB this gets me to the command line

I can remove quit splash and type nomodeset

Login screen for live boot
user = ubuntu
password = (leave blank) 

Screen flashes and tries to boot but then takes me back to boot screen again.
????

Please advise
Thanks

---

### Post by oldfred on 2015-09-21
If booting in UEFI mode you get a standard grub menu and have to edit the linux line.
Only with BIOS boot do you get the purple screen with the tiny accessiblity icons at bottom and press the "any" key to have menu where you can use f6 to choose nomodeset.

Also shows grub menu:
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by sudodus on 2015-09-22
> **AgentZ86 said:**
> Ok, I can hit TAB this gets me to the command line

I can remove quit splash and type nomodeset

Login screen for live boot
user = ubuntu
password = (leave blank) 

Screen flashes and tries to boot but then takes me back to boot screen again.
????

Please advise
Thanks

Now that you can enter nomodeset, try some of the other boot options too. Some particularly useful boot options are described in the first link in my previous post, and there is a long list in a link from that link ([kernel parameters](http://www.kernel.org/doc/Documentation/kernel-parameters.txt))

---

### Post by AgentZ86 on 2015-09-22
Ok, 

The flash boot I made with unetbootin does not have those same boot menu screens at all. It's totally different. It's a blue screen with text on it for selecting ubuntu options.
This is for usb boot. I do not need any uefi I have all this disabled in bios.

The netbootin method of creating the disk only allows to hit the tab to get to the command line. The F1-F6 keys, e keys will not get you anything for this. I have no idea why.

So here is what I did.
I used my other older machine that I was able to load 15.04 with the netbootin flash drive.
Then I used this machine to download the 15.04 ISO and recreate a ubuntu 15.04 flash using the start disk creator.

I then could boot and hit E for the options for nomodset and it booted perfectly. I installed it without problems as usual.
I then installed the nvidia drivers shown in the softwareupdates list without problem all worked perfectly as I expected it should.

It appear that unetbootin created it's own problems that could not be fixed or solved with commands either.

Thanks all for the help.

---

### Post by sudodus on 2015-09-23
I'm glad you found a method that works :-)

(It is possible that we don't use Unetbootin correctly. But at least, it should be possible to enter the boot options manually at the end of the 'linux line' or corresponding.)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

