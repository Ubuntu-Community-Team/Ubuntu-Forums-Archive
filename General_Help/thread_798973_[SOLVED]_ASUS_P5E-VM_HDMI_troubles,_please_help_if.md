---
title: "[SOLVED] ASUS P5E-VM HDMI troubles, please help if you can!"
date: 2008-05-18
forum: General Help
---

### Post by sickpunk on 2008-05-18
Hi everyone,
I recently finished building my first computer, and I would LOVE to have it running Ubuntu as my main OS.  The specs as of this moment are:

ASUS P5E-VM HDMI micro-atx motherboard (updated to most recent firmware 505)
Intel E8200 core2 processor
ATI Radeon HD2400 Pro
LG GGC-H20L BD-Rom drive
Western Digital hard drive
ASUS WL-138g V2 wifi card (Broadcom BCM4318 chipset)

I'm pretty sure my problem is my BIOS settings, but I'm not positive and could very easily be wrong.  

The problem?  I'm able to run the liveCD and get through the installer.  I reboot, get to GRUB and select Ubuntu.  The splash screen shows, then when the orange bar is all the way full, the screen goes blank and my monitor reports that there is no signal.

The reason I suspect that it may be my bios settings is because I had the same issue using the onboard graphics, which is the reason I bought the Radeon.  I know Ubuntu works on this MoBo, because I've read of other people's success.  I'm able to use Windows XP for now, but when I decided to build this I had my heart set on Hardy.  I'm just too new in the world of linux to figure it out on my own :-P

If you have any suggestions, or if you use this MoBo and could share your BIOS settings, or pretty much ANYTHING, I'd truly appreciate it!

Thanks in advance to anyone and everyone!

~Chris

---

### Post by ibuclaw on 2008-05-18
Try starting up in safe graphics mode.

When the LiveCD boots, select your language, then press "**F4**"

You should see something like the attached image below. (minus the top and bottom, I'm running it in VirtualBox).

Choose "**Safe Graphics Mode**", then continue to run the LiveCD.

Regards
Iain

---

### Post by sippnonacorona on 2008-05-18
I don't think Ubuntu 8.04 HARDY supports the Intel GMA X3500 chipset yet. The embedded video is not recognized. 

I found it necessary to use the generic VESA driver for now. I had to add "vga=795" to the boot options (F6?) at install time. This gave me a VESA standard screen set to 1280x1024 for my monitor. Look at [http://ubuntuforums.org/archive/index.php/t-212832.html]("http://ubuntuforums.org/archive/index.php/t-212832.html") for other possible settings. I also added it, using ```
sudo gedit /boot/grub/menu.lst
``` to the grub boot file. On the line that says ```
# defoptions=
``` I modified it so it looked like ```
# defoptions=vga=795
```. Then I ran ```
sudo update-grub
``` to process the update.

I also downloaded the Audio and Lan driver Linux source code for this mainboard from ASUS's site. Unfortunately, the instructions are for RedHat and SUSE. There are no instructions for Debian or Ubuntu on how to compile and install...:( I'm a newbie and haven't figured this out yet.

---

### Post by sickpunk on 2008-05-19
Well, I gave those options a shot... Still no dice!  I'm gonna try Gutsy and see if my luck improves at all.  Thanks for the suggestions!

---

### Post by sickpunk on 2008-05-26
I figured it out yesterday.  It had absolutely NOTHING to do with my Motherboard; I was using the VGA port on my LCD TV as my monitor, and it seems ubuntu was outputting a resolution not supported by my TV.  I just went into recovery mode, added a mode for 1280x768 and now I'm good to go!

Yep, I'm an idiot :-P

But now I have glorious, glorious Ubuntu on my previously plagued by windows box!  Thanks for everything everyone!

---

