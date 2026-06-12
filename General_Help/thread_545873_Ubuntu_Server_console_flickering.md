---
title: "Ubuntu Server console flickering"
date: 2007-09-08
forum: General Help
---

### Post by the ev on 2007-09-08
Title says it all, really.  I'm not running any sort of X, just straight console.  The text flickers; not enough to be unreadable, but enough to be extremely annoying.  If I boot to a Desktop LiveCD there's no flickering...smooth as butter.  Also, the boot menus (grub and otherwise), as well as the BIOS screen are all rock solid...it's only when I load into the Ubuntu Server installation that the flickering starts.

I have my menu.lst set to vga=795 (I have a 19in LCD, capable of 1280x1024).  The flickering happened before I made the change, and has persisted afterward, even though the vga switch successfully changed my resolution.  

I'm running Ubuntu Server 7.04. My graphics card is overkill for this sort of thing, and since it works with other Ubuntu-related stuff (the liveCDs), I don't presume that's the problem.  Any thoughts?

---

### Post by the ev on 2007-09-08
I'm guessing this is something to do with an incorrectly set refresh rate, but I can't find out how to change it!  All my online searches give me documentation on how to change it with X, but I don't have X.  Anyone?!? Please??

---

### Post by the ev on 2007-09-08
So I eventually stumbled upon SVGATextMode, which seemed to offer more control over refresh rates (among other things) in the console, and while every mode I tried to invoke invariably crashed the video out to my monitor, after restarting a few times the flicker is gone and everything seems to work.

Can't say I really understood what happened, but if anyone is having similar problems, download and install SVGATextMode and set the refresh rates specific to your monitor in the /etc/TextConfig file in the appropriate section...do lots of stuff, including rebooting...and you should be good.  ??

Oh well - it works; I'm not complaining. ;)

---

### Post by the ev on 2007-09-08
Oi - I spoke too soon.

Here's a kicker; if the machine has been off for a while, then I turn it on = no flickering for a few minutes.  Immediately rebooting = immediate flickering.

I still feel like SVGATextMode should offer a way to fix this, as I'm sure it's a refresh rate problem, but I can't find the chipset information for my Nvidia GeForce 7600 GT.  Per [http://www.linuxfromscratch.org/hints/downloads/files/OLD/svgatextmode.txt]("http://www.linuxfromscratch.org/hints/downloads/files/OLD/svgatextmode.txt"):

> V. Configuration
----------------
After installation, open the /etc/TextConfig file in your favorite editor.

!! READ THE HINTS AND WARNINGS AT THE TOP OF THE FILE !!

The default setting for SVGATextMode is standard VGA, which is highly sub-
optimal for most modern Linux systems.  You'll want to change the configuration
settings in this file to match your video card and monitor.  Down about line
60 of the TextConfig file is this text:

Chipset "VGA"
Clocks 25.175 28.322

You want to comment those lines out by placing '#' characters at the beginning
of the lines.  Then, scroll down through the (long!) list of chip sets to
locate the one that matches your video card.  Uncomment the line, and the
"Clocks" or "Clockchip" line for your card.  For example, I un-commented
these two lines for my S3 Virge based video card:

Chipset		"S3"
ClockChip "S3Virge"

Many of the pre-configured cards have additional settings with which you may
want to experiment.

IMPORTANT:  You should be absolutely sure about the kind of video card you have,
and specify it properly here.  If you have any doubt, get out the documentation
for your card, or examine the card itself to see what chips are on it.

After you have configured the video card, you need to tell SVGATextMode your
monitor's allowable horizontal sync and vertical refresh timings.

Find these two lines in TextConfig:

#HorizSync 30-32
#VertRefresh 50-80

These are defaults that will work with almost all monitors.  But most monitors
are capable of much more than this.  Uncomment these two lines and look in the
manual to find the allowable values for your monitor.  It's possible that those
numbers will be printed on the back of the monitor, as well.  It's very
important that you enter the correct numbers for your monitor here.  Failure to
do this can cause SVGATextMode to send signals that will fry your monitor.

Once you've made these changes, save the file and return to your console prompt.

Using lspci and trying to match the entry for my video card to the ones provided in the config file has gotten me nowhere - none of them seem to match!  Here's my card entry, courtesy of lspci:

> 01:00.0 VGA Compatible controller: nVidia corporation G70 [GeForce 7600 GT] (rev a1) 

Can anyone tell me how to find out what chipset section to use for my card?  Or shed some light on this whole debacle?

---

