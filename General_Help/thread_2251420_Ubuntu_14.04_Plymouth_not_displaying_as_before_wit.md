---
title: "Ubuntu 14.04 Plymouth not displaying as before with proprietary Nvidia drivers"
date: 2014-11-04
forum: General Help
---

### Post by JayArtist on 2014-11-04
Hi,
 

 I'm having issues trying to get the Plymouth boot screen to appear correctly in Ubuntu 14.04. I'm using proprietary drivers for my Nvidia card.
 

 This has always been an issue in Ubuntu as long as I can remember. In the past it was a matter of just modifying Grub and the image would load and the default low resolution font would be banished.
 

 But now it appears to not work so well.
 

 For safety I installed “Grub Customizer” (Editing Grub scares me!). In the “Appearance” tab you can specify the Grub image resolution, then alter the settings in the “Advance Settings”. Here's what I have currently:
 

 GRUB_DEFAULT				= 0

 GRUB_HIDDEN_TIMEOUT			= 0

 GRUB_HIDDEN_TIMEOUT_QUIET		= true

 GRUB_TIMEOUT				= 10

 GRUB_DISTRIBUTOR			= `lsb_release -i -s 2> /dev/null || echo Debian`

 GRUB_CMDLINE_LINUX_DEFAULT		= quiet splash

 GRUB_GFXMODE				= 1024x768

 GRUB_GFXPAYLOAD_LINUX		= auto

 

 

 So far on boot I get the Plymouth screen, but it always seems to default to what appears to be 640x480, which obviously makes the Ubuntu logo massive and pixelated. Whatever I change the resolution to, it makes no difference.
 

 In Grub command line I've found out the available resolutions “vbeinfo“, and there's obviously a varied amount of resolutions to choose from.
 

 Additionally if this can be fixed, is it possible to get a widescreen HD Plymouth with Nvidia Proprietary drivers installed? My resolution is 1920x1080. All of the listed supported resolutions are SD 4:3 resolutions making the aspect ratio wrong for the Plymouth screen. The Ubuntu logo obviously isn't round, it ends up oval which looks awful!  
 

 Thanks, Jay.

---

### Post by grahammechanical on 2014-11-04
How do I put this?

Grub is nothing to do with Plymouth and Plymouth is nothing to do with Grub. Grub will work with the basic video modes that the motherboard BIOS/UEFI boot system offers. Plymouth loads at some point after the Linux kernel has loaded. For all I know Plymouth may load before the proprietary video driver is loaded by Linux. We have an open source video driver that is there by default and I think that Linux makes use of that and then loads the proprietary video driver at which point we may notice a switch in resolution in the Plymouth splash screen.

There is something else going on that has an effect in all of this. Linux uses X the window system. In particular, the X.Org Server. At some point in the loading process the Xserver will query the EDID (Extended Display Identification Data) module in the monitor to get the optimum screen resolution and set the video driver to use that screen resolution.

So, you see a very complicated process is going on. It is a wonder it works at all. I do not think that altering Grub settings will fix your problem. 

I use an LCD TV as a monitor and that runs at 1920 x 1080 but the Grub boot menu is not full screen. There is a wide black boarder on all four sides of the screen. And this is even with a background image behind the Grub boot menu. At some point during the loading process the purple screen with the Ubuntu logo goes full screen. Usually, there is a black screen in between this happening. Which I put down to Xserver getting and acting on the EDID information. Things are as they should be by the time the LightDM (Light Display Manager) login screen appears.

I tell you something else. If I use a VGA connection to the monitor I do not get the 1920 x 1080 screen resolution. I have to use the HDMI connection to get the fine screen resolution that the monitor is capable of.

My point is that there are many factors involved and what I think is important is the resolution we get at the desktop.

Regards.

---

