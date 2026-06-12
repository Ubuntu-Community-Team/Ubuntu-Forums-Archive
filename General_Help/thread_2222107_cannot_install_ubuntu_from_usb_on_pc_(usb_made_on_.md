---
title: "cannot install ubuntu from usb on pc (usb made on mac)"
date: 2014-05-05
forum: General Help
---

### Post by carlos47 on 2014-05-05
I was messing around with EasyBCD on my PC, and somehow messed up my booting options, and even though I have Windows 7 perfectly installed on it, no matter what I do, I can't get it to boot.

My computer boots from Asus Aptio Bios.

I tried making an install USB for windows on my mac (the only computer I have left) using Bootcamp, and booting from it, but all I got was a blinking underscore upon choosing my USB to boot from. 
And since Ubuntu is a "hybrid" that can be run directly from a USB, I figured it would be nice to have *SOME* kind of operating system, instead of a totally bricked computer.

I downloaded the x64 iso from ubuntu, and used unarchiver to extract all of its contents onto the USB (making sure that all the files were correctly placed on the USB, after it was formatted for exFAT). 

Popped it into my PC's USB slot, pressed F2 for Aptio, chose my USB, and... What! Nothing? A blinking underscore again?!

Does my computer just... not recognize anything anymore, not boot from anything anymore, or what. It worked perfectly yesterday!
All I try to do is:
1) Download iso,
2) extract iso contents to formatted USB
3) put in computer
4) press f2 for BIOS
5) choose USB
6) blinking screen!

This is both for ubuntu AND windows 7 installs... someone amazing and knowledgable must help me!

---

### Post by HermanAB on 2014-05-05
No, that is not how it works.

For pretty much all Linux distros, you can simply copy the ISO file directly to the USB stick using a utility like dd (Linux/Mac) or rawrite (Windows) or rawwrite (Windows) - BUT NOT Ubuntu, since after all these years, the Canonical developers still haven't figured out how to make dual mode ISO files.

For Ubuntu, you need to use a special utility to prepare the USB memory stick as explained here: 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Sir_Ismicoo on 2014-05-05
> **HermanAB said:**
> No, that is not how it works.

For pretty much all Linux distros, you can simply copy the ISO file directly to the USB stick using a utility like dd (Linux/Mac) or rawrite (Windows) or rawwrite (Windows) - BUT NOT Ubuntu, since after all these years, the Canonical developers still haven't figured out how to make dual mode ISO files.

For Ubuntu, you need to use a special utility to prepare the USB memory stick as explained here: 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)


Using the command ```
dd if=ubuntu-14.04-desktop-amd64.iso of=/dev/YOUR_USBBKEY_HERE bs=4M conv=sync
``` worked absolutely fine to create a bootable usb key. I was also able to do the same for Xubuntu. You should not add a partition number to the end of YOUR_USBBKEY, for example, /dev/sdg not /dev/sdg1. I don't know whether this means other tools will also work.

@carlos47: When you first boot from the key, do you see anything or does it go straight to the flashing cursor? What happens if you press Esc?

---

### Post by carlos47 on 2014-05-05
Thanks! I used Unetbootin to create an Ubuntu USB from the latest 14.04 iso which will work on my PC. However, the same blinking underscore occurred.
It goes *directly* to a blinking underscore, and pressing escape and enter does nothing!

Like I said, I have also used BootCamp tutorials to try to bring back my Win7 OS, and I still get the blinking underscore.
I'm afraid my PC is now bricked because of EasyBCD!!

Please, tell me this isn't so~~!
I don't want to lose an entire $1500 computer for absolutely no reason.


I'm currently using unetbootin again, but instead of using the latest .iso, I'm selecting it from their pre-defined list of linux distros, and selecting "ubuntu 14.04_live". It's extracting the files right now to my USB... wish me luck ;_; And... Nope! It still doesn't work... I'm going to try using unetbootin to install Xubuntu or other things and see if they work... because literally... everything... gives me just blinking underscores &#12640;&#12640;&#12640; I'm using an 8GB USB formatted to FAT32.

Now I installed Super Grub Disk with unetbootin onto my USB... still blinking line! I wish *something* would come up! Even if it was "Hello World!" or "Sorry, this file is messed up" would be better than blinking lines all the time.

---

### Post by HermanAB on 2014-05-05
Note that it doesn't matter how the USB device is formatted, since it will be overwritten entirely.

Get a copy of rawrite.exe or rawwrite32.exe and use that to copy the ISO file of any Linux or BSD distro to the USB stick and it should boot.

---

### Post by Sir_Ismicoo on 2014-05-05
I'm afraid my Windows knowledge is nearly as outdated as my fashion sense. The last Windows OS i used was XP! Does Windows 7 come with an installer disk? If so you may be able to boot to recovery mode and restore the MBR from there. If you don't have a Windows 7 disk then [boot repair cd]("http://sourceforge.net/projects/boot-repair-cd/") seems to be recommended. I've never used it so I don't know how good or easy it is.

I've just looked up what easybcd is and while I don't dual boot with Windows, I don't think you will need it. The Grub2 boot loader that comes with Ubuntu should pick up your Windows install and add it as a boot time option during the installation process.

---

### Post by carlos47 on 2014-05-05
@HermanAB
I think your thingy might work, but unfortunately I'm limited to my mac :(

@Sir_Ismicoo
The Grub2 boot loader that comes with Ubuntu would be nice, if I could *get* Ubuntu in the first place!

I'm going to take a bunch of screenshots right now so you guys know exactly what I'm doing. I've used UNetBootin to make tons of USB's for me such as Ubuntu14.04_live_x64, Lubuntu, Super Grub Disk, Smart Boot Manager, etc, and so far, *all blinking lines*!

PICS:

First I format it !!
[IMG]https://i.imgur.com/cCpL105.png[/IMG]

Then I download with UNetbootin !! (This shows Xubuntu, but I've tried it with Ubuntu, Lubuntu, and other software and it still doesn't work !)
[IMG]https://i.imgur.com/ocCVDdk.png[/IMG]


It downloads and installs in my USB !!
[IMG]https://i.imgur.com/Q9R2ESx.png[/IMG]


Then I put it into my PC and select it !!
[IMG]https://i.imgur.com/Oec4zgO.png[/IMG]

Then... FAIL !! :C

---

### Post by Sir_Ismicoo on 2014-05-05
It might be because it is booting from eufi rather than bios. Most eufi systems have an option to boot in legacy or bios mode, probably somewhere under the advanced tab. I've never had much luck booting Linux disks using eufi even they say they are compatible.

As for my easybcd comment, that was just in case you had installed it as a pre-requisite to installing Ubuntu.

---

### Post by carlos47 on 2014-05-05
Well, @HermanAB, I think you had the answer for me awhile ago !!
And @Sir_Ismicoo, I think it is good you mention Ubuntu can help with bringing back my win7 !

What I learned from all this: Do not use Unetbootin !! It's total garbage @!

In your original link, there was "Making a USB", and if you scroll down, there is 
[https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick)
Which is how you make the USB from a Mac !!  Thank you !

I made it this way, and I can't believe it works, I'm so dumb!!

I'm so happy! Yay !!

---

