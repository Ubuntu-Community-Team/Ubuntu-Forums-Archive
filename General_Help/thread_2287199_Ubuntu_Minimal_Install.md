---
title: "Ubuntu Minimal Install"
date: 2015-07-17
forum: General Help
---

### Post by Anon_Kun on 2015-07-17
Hey guys, I'm trying to install Ubuntu with the mini.iso and it won't work. 

The installation process is fine, I get through it just easy, I partition the entire disk so it just installs Ubuntu and when I reboot, it comes to a black screen with a blinking white cursor. It's booting from the HDD, I'm sure of it. 

Anyone know what's wrong?

---

### Post by QDR06VV9 on 2015-07-17
You will need a desktop environment.
> [COLOR=#333333][FONT=Ubuntu]To install, boot your computer from the the mini iso and select "Install" at the prompt. You can then follow the instructions from the text-based installer. On the software selection screen, you can select from a number of collections of software such as different desktop environments (kde, xfce, etc), a multitude of different servers, multimedia creation tools, media center (mythbuntu), etc. You can also select "Manual package selection" which will take you to aptitude. You may also select nothing and just continue to finish the installation. If you selected nothing, upon reboot you will arrive at a cli prompt; from here you can fully customize your new system.
[/FONT][/COLOR]
Also See this [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by Bashing-om on 2015-07-17
Anon_Kun; Hello;

"one' bean in your profile, does this mean you are new to linux ?
If you are new, you sure jumped off the deep end of the pool in choosing to install from minimal.
We are here to throw you life preservers and as many ropes are needed to keep you afloat.
These tutorials will be of immense help and guidance, These are only guides and suggestions, it is up to you what you install on your system/ With the minimal install all you have initially is barely enough to boot the kernel and a wired internet connection. NOTHING more, you must determine what else is to be installed.
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
[https://xpressubuntu.wordpress.com/2014/02/22/how-to-install-a-minimal-ubuntu-desktop/](https://xpressubuntu.wordpress.com/2014/02/22/how-to-install-a-minimal-ubuntu-desktop/)

Hey, I run minimal install - build my own -

[INDENT][INDENT]if I can do it
[INDENT][INDENT][INDENT]you can too
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sudodus on 2015-07-17
Some versions of the Ubuntu mini.iso are better (easier to use). I suggest that you download from [the links described here](http://ubuntuforums.org/showthread.php?t=2230389&p=13211730#post13211730) (and I would recommend the version 14.04 LTS).

I think that the mini.iso only works in BIOS mode. If you computer has Windows installed in UEFI mode, you should install from one of the desktop iso files (64-bit alias amd64).

---

### Post by Anon_Kun on 2015-07-17
> **sudodus said:**
> Some versions of the Ubuntu mini.iso are better (easier to use). I suggest that you download from [the links described here]("http://ubuntuforums.org/showthread.php?t=2230389&p=13211730#post13211730") (and I would recommend the version 14.04 LTS).

I think that the mini.iso only works in BIOS mode. If you computer has Windows installed in UEFI mode, you should install from one of the desktop iso files (64-bit alias amd64).

Thanks, I'll try it. 

I've been downloading the 15.04 version from here [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD), is that a bad source? I don't know if I'm doing something wrong but after I try installing it, trying to boot it back from my USB is a pain, it's like the image doesn't exist anymore. 

Also, I'm going to be putting Unity on, can I do a minimal install of Unity minus the bloat?

---

### Post by sudodus on 2015-07-18
The md5sums match between 'your' and 'my' links for the mini.iso, so both of them should work (I checked for the version 15.04).

But there might be another problem, for example to find suitable drivers for the graphics or wifi. What happens if you make a minimal installation without selecting any (extra) package, not for desktop environment, not for server? You should get a basic installed system with a text user interface.

If you still get no response from the installed system, I suggest again, that you try the version 14.04 LTS.

If you tell us about your computer hardware, it will be easier to give you relevant advice. So please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

---

### Post by Bucky Ball on 2015-07-18
Go for 14.04 LTS. Smoothest ride and longest support (until 2019). Make sure you have a solid ethernet connection, not wireless. Download the mini.iso from the BitTorrents [here]("http://www.ubuntu.com/download/alternative-downloads"). Best and safest way. If not up with torrents, get the .iso from the same site.

Create the live media, boot from it, install (don't choose a pre-defined system/tasksel), reboot and you should have a CLI to log in. Log in. Now you can install whatever you like. A basic start would be:

```
sudo apt-get install xfce4 synaptics firefox pcmanfm lightdm
```

That would give you a desktop environment so you can find your way around, a package manager to install other stuff as you need it, a web browser, a file manager and a desktop manager. The rest is down to research and asking questions. ;)

The mini is a steep learning curve from where you're standing, but when you break it down, pretty easy, so if you're up for it and want to go that way, more strength to ya! You'll certainly know about Ubuntu by the time you've got the machine ticking as you like. I, for one, am more than happy to help when I'm about. I only use the mini.iso, even when I install on other people's boxes. You can get exactly what you want. Good luck. :)

PS: The mini may not work with EFI, that is something I can't comment on as never tried.

---

### Post by Anon_Kun on 2015-07-18
When I boot from the USB after installing, it works. I can hit ALT+F1 and open the terminal. 

It doesn't seem to save to my HDD though, because I can't do anything without the USB in or booting from the USB with the image on it. It seems like it saves to the USB rather than the HDD, because when I try re-using the image, it doesn't work and brings me to the grub menu . The options are also a bit vague. 

It wants to resize my USB drive or partition it, I always use "Use entire disk" and select my HDD. It makes sense right? Well apparently something goes wrong or it happens to put it on my USB because for some reason, I can only boot from the USB. Perhaps I'm doing something wrong?

---

### Post by Bucky Ball on 2015-07-18
Choose 'Something Else' and create a 20Gb / partition, a /home partition as big as you like and a 2Gb /swap partition at the end of the drive. Proceed and the install will do the rest. 

/ and /home should be EXT4 filesystem and /swap will make itself swapspace when you set it as that rather than EXT4. [This]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352") might help. Good luck.

PS: You can delete the existing partitions once you get to the partitioning section of the install and choose 'Something Else'. Kill what you want and then make the partitions I suggested.

Is this install in UEFI or legacy mode? It makes a difference. Check the BIOS. If you are booting in EFI and are wiping the drive, best to add a small, say 200Mb, FAT32 partition somewhere which the install should automatically use as the EFI partition (you will need one).

If installing in legacy, make sure you have secureboot and EFI things off in the BIOS and install as per normal, choosing 'Something Else' when you get there and no FAT32 EFI partition.

---

### Post by sudodus on 2015-07-18
Yes, it seems you are installing to USB, at least the bootloader.

Are there more than one USB drives connected?

Can you still boot the mini.iso system from the USB drive?

If you tell us about your computer hardware, it will be easier to give you relevant advice. So please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

---

### Post by Bucky Ball on 2015-07-18
As above from sudodus. Just adding to my last post, I meant to say choose 'Something Else' and then you can install to the hard drive because you can choose exactly where you want to install. You will be able to see where it is going. As sudodus says, sounds like you're installing to the USB.

---

### Post by Anon_Kun on 2015-07-18
I finally got it to work. 

I just remove the USB when I partitioned the drives, and basically gave it no other option to put GRUB onto. 

Apparently I have network-tools installed, but can't connect via wifi. I know in Arch I'd do wifi-menu, but it doesn't work in Ubuntu. Any suggestions?

---

### Post by sudodus on 2015-07-18
See this link: [Unmanaged Wired Network](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Unmanaged_Wired_Network)


If you install Lubuntu (lubuntu-desktop or lubuntu-core) you will get network-manager, and it should work and help you connect via wifi.

---

### Post by Bucky Ball on 2015-07-18
Install network-manager-gnome

```
sudo apt-get install network-manager-gnome
```

Reboot. You need to be online with an ethernet cable to do this. Pull the cable out when you reboot.

Your issue might be drivers for your wireless device though. With the cable plugged in and after an update, check 'Additional Drivers'. If nothing there for your wireless, givet the output of:

```
sudo lshw -C network
```

Thanks.

---

