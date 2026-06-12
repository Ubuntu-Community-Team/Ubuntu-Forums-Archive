---
title: "Installing Xubuntu on a Panasonic Toughbook CF-29E - no partition table in Live mode"
date: 2015-02-06
forum: General Help
---

### Post by egsauer on 2015-02-06
Greetings,

I am new to installing Ubuntu and have a Panasonic Toughbook CF-29E that I am working on. It is a project that I think will be interesting.
The laptop had no HDD, CDROM and only 256M of RAM. I scavenged a 10Gb IDE drive from a Tecra and hung that drive off of my work laptop to
install an image (smaller alternate version - I thought it was 14.04, but a uname -a says 3.13.03-24??) using Linux Live USB creator. I upgraded the RAM with a 1Gb module from Crucial - they were able to map my machine to the correct RAM module. I then installed the HDD in the CF-29 and booted it. Worked through the forcepae issue and got to the install choices. Selected Live and it comes up nicely. The touchscreen actually works! It even prompted me for a WiFi SSID - which now works. Sweet.

So far so good.

At this point I launch the installation and select none of the optional stuff and get to the partition page. Which is empty.

I cannot add or modify the partition table. I open a terminal and ran df -k and see that the system has mounted /dev/sda1 on /cdrom. Hmm, ok, I guess.
But how do I install Xubuntu persistently on my HDD? Did I miss a step, should I have set up multiple partitions from the Live USB creator? I do not recall that option.

I do not want Windows on this system, just pure Xubuntu. Can I use what I have to install from the network to the drive? I am guessing that Live is in RAM so what are my options? It's a cool, but dated laptop my kid wants to use in his car for OBDII monitoring. And this project is a preliminary for me as I want to build a NAS soon on a tower platform using linux.

I realize I am a newbie in this space so chances are it's a mechanical problem, loose nut behind the wheel, but I do have a reasonable understanding of some of this as I come from a Solaris SysAdm background.

Any Ideas and/or direction would be greatly appreciated.

Cheers,

Ed

---

### Post by JKyleOKC on 2015-02-06
The "live CD" version, even when moved to a flash drive and booted from there, should give you a desktop option to "install" on the hard drive. You are correct that the initial live version is running from RAM, but with a gigabyte of RAM you should have plenty of room for an install.

The 10-GB hard drive is pretty small for today's software, but should be ample for the installation if your son doesn't install many additional packages. The actual system will probably need half that space.

I'm not familiar with the specific unit you're using so cannot help with the mapping to /cdrom -- you may need to go into its BIOS to force booting from the USB port. However if you do manage to get into the installer program of the live CD package, you need to select the "Something else" option when it gets to the "where to install" dialog. This is where you get the opportunity to format the hard disk and select partitions. Hopefully, "oldfred" will jump in here and give you a number of links to step-by-step instructions. I don't keep the huge library of links that he does, but as a user of Xubuntu for almost a decade now I'll be happy to help you in any way I can...

---

### Post by egsauer on 2015-02-07
Thank you Jim. I have attempted the "Install" and that is where I ran into the blank partition table. Once the installer program starts it gives me the WiFi connection page and then the Welcome and next the Preparing to Install pages followed by this partition table in a page titles "Installation Type", but there is no "Something else" option on that page or any before it. Here is what I see (image attached). The /dev/sda is the only item available in that "Device for boot loader installation" drop down . When I select "Change" the Installer just quits. When I select "Continue" the installer crashes with a Ubiquity internal error in the partman module. Hoping this info helps you and that "oldfred" can chime in because it does sound like a partitioning issue.

Thanks again, I appreciate your help.

---

### Post by westie457 on 2015-02-07
From what I understand in this > [COLOR=#000000]I am new to installing Ubuntu and have a Panasonic Toughbook CF-29E that I am working on. It is a project that I think will be interesting.[/COLOR]
[COLOR=#000000]The laptop had no HDD, CDROM and only 256M of RAM. I scavenged a 10Gb IDE drive from a Tecra and hung that drive off of my work laptop to[/COLOR]
[COLOR=#000000]install an image (smaller alternate version - I thought it was 14.04, but a uname -a says 3.13.03-24??) using Linux Live USB creator. I upgraded the RAM with a 1Gb module from Crucial - they were able to map my machine to the correct RAM module. I then installed the HDD in the CF-29 and booted it. Worked through the forcepae issue and got to the install choices. Selected Live and it comes up nicely[/COLOR] You have put the ISO onto the HDD. If that is a correct assumption then the installer will not see the hard drive and is probably the reason it has been mounted as /dev/sr0.

---

### Post by egsauer on 2015-02-07
Yes, I put the ISO on the HDD because the Toughbook has no CDROM and cannot be configured to boot from a USB.

If that is why the installer is not seeing the HDD is there any work around with this setup? Or do I need to try a different approach like
finding a CDROM for this laptop and booting the installer from that figuring out how to boot from the network somehow. I have a Sun Blade on this network so it may be feasable to configure that as a TFTP Boot target, but I would need to find the destructions for setting that up from the laptop side.

Could I buy a larger HDD (IDE for this beastie) and partition it before I load the ISO to one of the separate partitions?

It seems so close right now, but so far away without any disk to install to.

Thanks for the feedback.

---

### Post by mörgæs on 2015-02-07
Have you checked if there is a newer BIOS available which supports booting from USB?

Another option is moving the hard disk to another computer, do a standard install there and move the disk back.

---

### Post by egsauer on 2015-02-07
> **mörgæs said:**
> Have you checked if there is a newer BIOS available which supports booting from USB?

Another option is moving the hard disk to another computer, do a standard install there and move the disk back.

There is a newer BIOS, but it is only installable from Windows. It only updates the EDGE/EVDO features and not, from what I can tell, the boot from USB feature so no loss really.

Your suggestion to move the hard disk to another computer and install Xubuntu from there is the route I am going to take. Simple, easy, and something I can do with what I have. I'll report back if it works - probably today or tomorrow.

Excellent suggestion! Thank you.

---

### Post by egsauer on 2015-02-12
A quick update.

Making progress, but had some hurdles. I brought a Dell E521 from a friend out of mothballs to install the 2.5 disk on and use a USB with Xubuntu to boot the installer. The E521 couldn't see anything but the USB as sda. Turns out the E521 IDE controller has problems so I hung the 2.5 from a SIIG USB kit and plugged that into the front USB port alongside (ok, under actually) the Xubuntu boot drive. The installer finally saw the 2.5 drive - yay - and I was able to format the drive. I am now installing the base system and plan to take that and install the drive back into the Toughbook and boot. I will work out installing additional packages from there.

Fingers crossed!

Thanks again for helping me make progress on this folks.

Ed

---

### Post by egsauer on 2015-02-14
Update on Mr Toad's wild ride ...

Loaded xubuntu 14.04 on a usb drive.
set up my 10Gb drive as a usb drive.
plugged both into the Dell e521 I had for this adventure.
Booted, got the installer and stepped through that until I got to the partition section.The installer saw both usb drives, the Live on on sda and the disk as sdb.
Selected the sdb drive for partitioning and all seemed to go well.
Installed only the xfsce desktop package. That could have been a mistake.
Stepped though to the grub section and grub only listed the sda device. Aborted the installation and tried again, and again, and ...
Gave up on using the Dell e521. 

Moved both Live usb and 10Gb disk to my E6510 (Windows 7) system.
Booted from the USB with the live 14.04 installation kit.
Again all went well up to the grub installation and again grub only displayed my internal drive.Not an option. 
Skipped grub, went to Lilo, 
Lilo saw the 10Gb hanging off of the usb so I installed using lilo 

Moved the 10Gb to the Panasonic Toughbook CF-29, installed it as the internal HDD and booted.
It fails with the PAE error and just kind of hags there. Ok seen that with live on this box before.
Reboot, looking for the little dude icon so a tab can get me where I can add "forcepae" to the boot args. No joy.
Boot again and hit "shift" before the Lilo "........" and it pops to a boot: prompt.

boot: LINUX root=/dev/sda1 forcepae <ENTER>

The ramfs boot version had /dev/sdb1 as the root, but that was no sda1

boots to a command line interface.

At this point it looks like nothing more than basic is configured - possibly even loaded - no network interfaces are up, cannot startx, no man pages, but I can login with the user/pwd I gave it at install and I can sudo so I feel I am actually pretty close. I was spoiled by the Live system I originally had on the drive. It came up with the GUI, connected to the network via WiFi, touch screen even worked. This install may take a lot of work to get there. I suspect I will need to start with network so that I can get packages.

Would it be better to go back and redo the installation from the Win7 system and add packages? If so then is there a way to see what the Live version has on the USB drive in terms of packages?

Cheers,

Ed

---

### Post by mörgæs on 2015-02-15
> **egsauer said:**
> no network interfaces are up

Does that mean that you get neither wired nor wifi connection?

---

### Post by egsauer on 2015-02-15
Yes, When this installed version boots it has no wired nor wireless connection set up.
In addition it is missing things like startx and man.

Because this laptop has no CD-ROM and cannot boot from USB I am forced to remove the hard drive and hang it as a USB drive from my Windows 7 laptop to install the xubuntu on the hard drive. During the install grub failed to see the USB hard drive so I used lilo. I also chose not to install any packages other than th xfsce desktop - probably why there is no startx nor man. I am going to redo the install from my Win7 system and add the packages and see how it goes.

Cheers,

---

### Post by mörgæs on 2015-02-15
Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by egsauer on 2015-02-21
I was able to resolve this problem once I reviewed the lshw.txt output. 

Note  that what I was trying to do was install Xubuntu on a hard drive that  had been removed from a Panasonic Toughbook CF-29 and installed as a USB  drive on a system that supported USB booting. I had Xubuntu 1404 loaded  on a USB flashdrive and had booted from that USB flashdrive. The goal  was to install Xubuntu to the USB hard drive, remove that USB hard drive  and re-install it in the Panasonic Toughbook as the internal hard drive  and boot xubuntu from that drive.

During the installation  process in the grub steps, the installer presented the local disk, sda,  as the target for grub installation and also detected only a MicroSoft  OS as installed. I had originally responded with "Yes" and continued at  this step, but that resulted in a black screen boot on the Toughbook.

I  had to re-install the Toughbook Hard drive as a USB drive on the second  system and go through the installation a second time. But this time  when grub asked if sda was the system to install to I did not proceed.  Instead I chose "No" and in the next screen the other disk was displayed  (sdb). I chose that disk and completed the installation, installed the  disk in the toughbook and it boots successfully.

I am sure it was my error or more than one that was the issue, but it just took time to fill in the blanks. 

Thank you one and all for your inputs.

---

