---
title: "Unable to install Ubuntu 13.04 Desktop on new PC"
date: 2013-04-27
forum: General Help
---

### Post by yesmat on 2013-04-27
Hi All,

I have bought a new PC hardware in order to install Ubuntu 13.04 Desktop, but was unable to install it.

I downloaded the new iso "ubuntu-13.04-desktop-i386.iso", burnet it on a DVD and booted to it.

Most times I never get passt the word "Ubuntu" with the dots scroling underneath it, other times i managed to get passt that and clicking on "Try Ubuntu" i get to the desktop after long time.

The new motherboard that I am using is a Gigabyte F2A85XM-D3H with a AMD processor, 20GB SSD, 8GB RAM, and a dual UEFI BIOS.

I finally got tired and installed Linuxmint 14 in 10 minutes without any problems what so ever.

Any one has experienced issues of that kind?

many thanks

---

### Post by carl4926 on 2013-04-27
UEFI requires you use 64 bit any way
You may also need to use nomodeset boot argument
See also: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by sanderj on 2013-04-27
> **carl4926 said:**
> UEFI requires you use 64 bit any way
You may also need to use nomodeset boot argument
See also: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

FWIW

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) indeed says "If you have a PC with the Windows 8 logo or UEFI firmware, choose the 64-bit download.". I would find it useful if the i386 Ubuntu version would check for UEFI, and if so, bail out and advice the 64-bit version. Just like the 64-bit install does when you try to run it on 32-bit

---

### Post by sudodus on 2013-04-27
> **sanderj said:**
> FWIW

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) indeed says "If you have a PC with the Windows 8 logo or UEFI firmware, choose the 64-bit download.". I would find it useful if the i386 Ubuntu version would check for UEFI, and if so, bail out and advice the 64-bit version. Just like the 64-bit install does when you try to run it on 32-bit
+1
Good idea :-)

---

### Post by sudodus on 2013-04-27
I was adviced to report it as a bug in Launchpad (with credit to *sanderj*)

Here it is:  [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173527](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173527)  

Please add 'This bug affects me' if you feel like it

---

### Post by yesmat on 2013-04-28
Many thanks for all your replies. I will try tonight to install the 64-bit version, my only worry now is that my brand new motherboard and CPU may not support 64-bit. Will report later tonight anyway.

One thing worth mentioning is that my BIOS supports both modes of operation. There is actually a setting in there that allows me to change the mode of the BIOS and chose one of the following options:

UEFI+Legacy
UEFI only
Legacy only

The default setting was UEFI+Legacy, and I did change it to "Legacy only" and I still had the same problem.

The point that I would also like to mention to "Sanderj" is that there are no logos on the PC, i purchased all the parts and put the whole thing together.

Thanks

---

### Post by rrnbtter on 2013-04-28
Greetings, 
Gigabyte F2A85XM-D3H I would find it amazing if this were not a 64bit board. It even supports memory configurations that haven't been developed yet via bios/firmware update.  Legacy just means non UEFI and NOT non advanced 64 bit architect. With a UEFI board in most cases you will need a 64 bit system even with UEFI turned off (legacy). Some boards may not support linux in either case.

---

### Post by Bruno Augusto on 2013-04-29
I have a similar problem. December last I bought a new computer to replace an old one and I would really like to test Linux for the first time.I tried with 12.04 and now with 13.04 and I can't get into the installer. I boot up the PC with DVD in drive, the isolinux is loaded, the purple screen is shown but after that I have a black screen with a yellow dollar sign in a red background, frozen.My configuration (most important, at least):Intel IvyBridge Core i5 3.7 Ghz.8G RAMHD 500 GBMoBo: ASUS P8H61M-PROThe first time I tried (12.04) I remember I downloaded the ISO several times, I burned it several times, in different disks (R and RW) in different computers, tried to install it in a flash drive and nothing worked. This time, however, I tried just once, in DVD-RW disk.

---

### Post by yesmat on 2013-04-29
I have downloaded and burned the 64-bit version on a DVD.

I now can boot from the dvd. But I am still getting funny behaviours while trying it without installing. All icons on the vertical launch bar keep flickering all the time, especially when hovering the mouse over them, some disappear momentarily leaving an empty square box until they come back again. 

I have changed the BIOS to different settings and no matter what I did, the behaviour is still the same, tried UEFI only, UEFI+Legacy, none of it work OK.

And to add to the problem, i burnt the older 32-bit 12.04 version and to my dismay i had the exact same behaviour, which indicates that it could be a hardware issue relating to the new motherboard and/or chipset. Upon contacting Gigabyte, they replied that the board doesn't support Linux since the chipset manufacturer didn't supply any drivers for Linux, what a load of....

Linuxmint 14.0 installs like a dream in 10 mins and works perfectly, but using Linuxmint to me feels like going back in time, I would rather use Ubuntu and unity instead.

Any ideas where to go from here?

Thanks for your support.

---

### Post by carl4926 on 2013-04-29
Use what works or you are going to get very frustrated

---

### Post by sudodus on 2013-04-30
If you enjoy the challenge,

- try some boot options, [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

- and if you install a system, try with different versions of proprietary drivers for the graphics chip/card,

- check also if it is a wifi driver, that is interfering (by switching off the wifi if this is relevant)

otherwise, stay with the working Linux Mint version (it is Ubuntu under the hood).

---

### Post by yesmat on 2013-05-01
Certainly will try the different boot options and see where that take me.

i will probably use clonezilla to backup my entire Mint install to go back to at the end if Ubuntu failed to install and work properly.

It is a challenge OK, but i find this strange that Ubuntu are not paying attention and fixing install issues like this one, this will push away at least some potential users to using other distros and possibly never coming back, especially when another distro, completely based on Ubuntu, install and works flawlessly.

Thanks for your support and help.

---

### Post by gtc on 2013-05-02
Any one has experienced issues of that kind?


Yep.
I also bought a whole swag of new stuff to make a box for 13.04. 
I have a Gigabyte GA-970A-D3 motherboard, nvidia PCIe graphics card...  different problems / similar results...

I have been running Ubuntu for over 6 years now, generally doing a clean install with each release, so I am not a complete newbie at this :)  As other replies have mentioned, you need the 64 bit version for EUFI, but I have 8 Gb RAM so had that in any case.

First try got past the Ubuntu logo with the dots, but I could do nothing when it came to the first screen after that offering try or install.
Much hair pulling later, I discovered that once the initial screen was past - where mouse and kb did work - there was no USB or network on the board - so no mouse or keyboard (USB) and no internet to possibly get the solution during install.
The board has a PS/2 socket, so a keyboard could be made to work, and eventually a PCI network card allowed the install to get further - but still no USB or m/b network, and trying to get around without a mouse is painful. 

Suspecting the EUFI BIOS, I tried changing stuff about... no change. After a BIOS update and many resets following changing settings to try and get around this issue, the final result was basically the default - ensuring that the UEFI setting was set to both EUFI and Legacy... and letting it figure things out...

Wondering if I had some dud hardware, I did a quick load of Win 7 on another drive - everything worked fine. I have a USB stick with a bootable copy of gpartedmagic  - that worked fine, USB and network all good. I then tried debian 6.0.7 and that too installed fine with everything working ( and looking like my fallback OS! - but I would have to work on getting gnome3 going, the gnome2 it comes with is a tad too retro for me :) )

.... I thought Ubuntu was based on debian ?... what have Ubuntu broken/changed to make their install this... obstructive ?... 

After the passage of days, much gnashing of teeth and searching of the net, I stumbled across a mention of IOMMU, in that it had to be enabled. By default is is disabled on the gigabyte board and I had left it that way. So I enabled it... and surprise!... the USB and network worked...     

One of the problems left is that at the end of the install the message says to reboot, you click continue and the disk is ejected... and nothing... it just sits there with a blank screen. No keyboard or mouse input makes any difference. Eventually I press the reset and it boots up, asks for my password and loads a totally blank desktop - just the default purple-ish background but nothing else. Keyboard shortcut gets me to the command line and I use apt to load the gnome shell... so far - about an hour - it seems ok.... but I may try again to see if I can get around the blank screen...

And it seems to not be seeing all the RAM... it has 8 Gb, but is only reporting 3.8 (we will call it 4 )Gb....

Any suggestions on another motherboard brand ?... one where the manufacturer realises that the world does not consist of MS Windows alone and/or  actually gets the UEFI thing right ???

Cheers.

---

