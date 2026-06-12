---
title: "How do you wipe an encrypted disk for a complete new installation?"
date: 2014-11-04
forum: General Help
---

### Post by jamal5 on 2014-11-04
Hi all,

Right now I have Ubuntu 14.04 installed with full disk encryption. I'm looking to get rid of my current system and install Xubuntu, wiping everything. If I were to try to install from a live CD, it wouldn't let me run the live os since the cd only has access to the ~100MB boot partition.

How do I go about installing a new OS from scratch on my encrypted computer?

Thanks for the help

---

### Post by Gordonbp531 on 2014-11-04
Live CD's run in RAM not on the HDD.
You don't need any access to any partition at all to run a Live CD.
Boot up from the CD and use GParted to remove the existing partition(s).
(In fact the Install dialog will allow you to replace everything on the HDD without using GParted)

---

### Post by rbmorse on 2014-11-04
From the liveCD start 

gparted

and once gparted loads, select the disk you want to manipulate from the pull-down in the upper right.  Once you select a device, right click in any part of the graphical partition map, or on the partition entry in the list below and select "delete."   Then click on the green arrow icon in the menu bar to confirm the selection and execute the action.  Repeat on any remaining partitions. 

The Ubuntu family installer can use an unpartitioned disk, so to perform the install just close gparted and select "install Ubuntu (whatever) from the desktop icon and follow the prompts.  When you get to the partitioner screen select the empty disk as the target for the installation.

---

### Post by dry crust on 2014-11-04
As I understand it, you could just do a normal "only Ubuntu" installation, where you use the entire HDD. That will, of course, completely erase whatever is currently on the HDD, so make sure you have backed up everything, including the email addresses and memorised important passwords. My understanding is whatever is on the disk before you do the installation is lost. 
I recently forgot to get some data off a HDD before I installed the new OS, and decided to try and recover it, so I downloaded System Rescue cd but it couldn't see anything. Oh, now I remember, I wanted to try CentOS first, so I downloaded that (4GB) and installed that, and then decided to use Ubuntu-Gnome instead, so I downloaded that and installed that, and then tried to recover the data ... but system recovery disk couldn't see past the Ubuntu-Gnome installation, it couldn't even see that I had installed CentOS previously, let alone the Linux Mint I had the day before. That was the first time I had used System Recovery, so I can't say whether it was me, the System Recovery CD, or the completeness of the Ubuntu installation process, but my guess is System Recovery isn't at fault. 
If you wanted to be extra cautious why not try and recover the information off your HDD yourself? Maybe you could try and do an installation doing a fresh encryption first (even though there isn't enough room on the HDD for normal use), and then do a second installation using just the default settings.  
As I understand cryptography, every time you use a code for a letter that code goes "to the bottom of the pile", so that particular code is only used again after 64K (or however many) uses to mean that particular letter. If so, then if you encrypt the disk again, then whatever was on the disk will have no meaning to the current installation as a completely new set of cryptographic codes will have, or rather should have, been used. 
As a thought, had you considered replacing the HDD for a larger one?

---

### Post by jamal5 on 2014-11-06
> **rbmorse said:**
> From the liveCD start 

gparted

and once gparted loads, select the disk you want to manipulate from the pull-down in the upper right.  Once you select a device, right click in any part of the graphical partition map, or on the partition entry in the list below and select "delete."   Then click on the green arrow icon in the menu bar to confirm the selection and execute the action.  Repeat on any remaining partitions. 

The Ubuntu family installer can use an unpartitioned disk, so to perform the install just close gparted and select "install Ubuntu (whatever) from the desktop icon and follow the prompts.  When you get to the partitioner screen select the empty disk as the target for the installation.

The problem is that my system refuses to boot from the live CD

Upon turning the computer on, I can hear the disk drive  (Xubuntu Live cd inside) spinning loudly for a good minute, but instead of booting from the disk, it just puts me in the GRUB menu and stays there.  GRUB lets me choose from

*Ubuntu
Advanced Options     (which lets you choose recovery mode)
System Setup       (lots of different menus here, I can't find any solutions to my issue though....)

And at the bottom it tells me I can press 'e' to edit the options or 'c' to get a command line (which is the grub command line)- do you maybe know the command to get it to boot from the media? Pressing Tab  gives me a list of about 50 different commands, none of them seem like they have anything to do with booting from a livecd, there is a 'usb' command though, maybe it's for liveusb's??

I've restarted it a bunch of times and it keeps giving me the same thing. I even tried booting from a different live cd with TAILS on it to see if it isn't a problem with the specific disk, but it does the same exact thing....

---

### Post by coldcritter64 on 2014-11-06
> The problem is that my system refuses to boot from the live CD

Upon turning the computer on, I can hear the disk drive  (Xubuntu Live  cd inside) spinning loudly for a good minute, but instead of booting  from the disk, it just puts me in the GRUB menu and stays there.  GRUB  lets me choose from

You need to access the BIOS or UEFI screens prior to the Grub boot screen to set the machine to boot from a cd.
To access setup (BIOS or UEFI screens) you need to press a key (varies between machine manufactures) like F2 or delete etc to get the hardware set up screens. BIOS/UEFI is skipping looking for the cd drive and going straight to Grub because of hardware set up values by the sounds of that.

The key to press will be shown (usually) on the first of the POST screens prior to grub loading. Mine says something like "Press F2 to enter set up". Look for a message like that and follow it.

Edit: look for settings for "boot order" or similar, you may have to dig through the settings to find it. Put the CD drive in 1st spot there and save the settings and reboot.

---

### Post by jamal5 on 2014-11-06
> **coldcritter64 said:**
> You need to access the BIOS or UEFI screens prior to the Grub boot screen to set the machine to boot from a cd.
To access setup (BIOS or UEFI screens) you need to press a key (varies between machine manufactures) like F2 or delete etc to get the hardware set up screens. BIOS/UEFI is skipping looking for the cd drive and going straight to Grub because of hardware set up values by the sounds of that.

The key to press will be shown (usually) on the first of the POST screens prior to grub loading. Mine says something like "Press F2 to enter set up". Look for a message like that and follow it.

Edit: look for settings for "boot order" or similar, you may have to dig through the settings to find it. Put the CD drive in 1st spot there and save the settings and reboot.

Hi,

I got to the BIOS screen, scrolled over to the Boot sections, and it seems like there&#347; no option to change any of the settings. Here&#347; a pic of my screen:

[ATTACH=CONFIG]257777[/ATTACH]


All the choices are grayed out which means I cant select anything, the choices blue in the other menus where you can select them... The MATSHITA DVD... is my dvd drive which is what I want... Any idea of what to do?

Do you think trying to boot from USB might work instead or would it just be the same exact thing? I would have tried already that but I&#7743; worried the USB will turn to read-only mode and become unusable for anything else like dvd&#347; do when you put a live os on them, I dont care about a 25 cent DVD but I dont want to waste a $20 usb stick.

Thanks for the help so far

---

### Post by coldcritter64 on 2014-11-06
Using your keyboard arrow keys see if you can highlight the 3rd or 4th entry (not sure which to use, both refer to the dvd drive). Then  the +/- keys will move the entry up or down the order. Put the dvd entry in No. 1 spot and press F10 etc to save the settings and reboot. 

BIOS/UEFI screens are keyboard centric and can take a bit of getting used to. That should get the dvd/cd drive booting. Try both entries out and reset to as it is now when you are finished (will stop accidental cd/dvd booting later on, a nuisance at times if you forget that setting).

Edit:Yes booting from usb may be possible but will need the boot order set in the hardware settings as well, usually needing a couple of settings changed, can be harder than cd at times to set up.

---

### Post by Impavidus on 2014-11-06
> **jamal5 said:**
> Upon turning the computer on, I can hear the disk drive  (Xubuntu Live cd inside) spinning loudly for a good minute, but instead of booting from the disk, it just puts me in the GRUB menu and stays there.If you hear the dvd spinning for a minute but then the computer boots from the hard drive anyway, it could be that you just have a bad or dirty dvd (or a bad dvd drive). After trying the dvd, the system gives up and moves on to the next drive in the boot priority list. Cleaning might help, or burning a new disk.

> **jamal5 said:**
> 
Do you think trying to boot from USB might work instead or would it just be the same exact thing? I would have tried already that but I&#7743; worried the USB will turn to read-only mode and become unusable for anything else like dvd&#347; do when you put a live os on them, I dont care about a 25 cent DVD but I dont want to waste a $20 usb stick.
Later you can simply format the usb drive again and use it as before.

---

### Post by jamal5 on 2014-11-06
> **Impavidus said:**
> If you hear the dvd spinning for a minute but then the computer boots from the hard drive anyway, it could be that you just have a bad or dirty dvd (or a bad dvd drive). After trying the dvd, the system gives up and moves on to the next drive in the boot priority list. Cleaning might help, or burning a new disk.


Later you can simply format the usb drive again and use it as before.

It's not an issue with the DVD drive since the iso seemingly burned to the disk fine, and I can read files off of disks without problems. I have a live CD of Tails that I've used before successfully on a different computer- so I know the disk works- I tested that and it just gave me the same result as the Xubuntu disk- the grub menu

I can't navigate through the BIOS Boot order menu because the options are grayed out (as in the pic) and it won't respond to arrows or +/-.  Under the other menus, some options are blue some are gray, and the arrows can only select the blue ones and skip over the gray.... Is there a way to reformat the hard drive or something else to force it to go through?

---

