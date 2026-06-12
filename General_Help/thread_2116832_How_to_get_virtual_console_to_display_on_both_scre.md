---
title: "How to get virtual console to display on both screens in dual head?"
date: 2013-02-16
forum: General Help
---

### Post by georgelenzer on 2013-02-16
In the past I was able to view the same virtual console on both screens in a dual head set up.  When I moved to a laptop with an Nvidia GPU in it (just like the desktop), the VGA out would go dead unless I was in X.  As soon as I would hit Ctrl-Alt-F1 through F6, the external monitor would go black.  Annoying because the monitor in my laptop is dying, but I've been living with it.

Just last night I upgraded to Ubuntu Studio 12.10, and noticed that during the installation, if I pressed Ctrl-Alt-F1 to get a virtual console, that it would display on both screens!  I also noticed that the X setup (likely using X's vesa, fbdev, or nouveau drivers) did a mirrored setup.

So this led me to experiment with Grub's gfxmode setting to see if I could get the right mode to allow both the internal and external monitor to display.  But none of that worked.  I could change the resolution of the initial grub screen or even turn off the "graphical console" in favor of the text console, but I never got anything that would turn on the VGA out.

I experimented with 640x480, 1024x768, and 1280x1024 as well as just the text console.  But, none of that worked.  Since it worked during the installation, something tells me that this is just a matter of getting the right mode set, or the right format of output for virtual console.  Any ideas?

---

### Post by georgelenzer on 2013-02-19
Any ideas anyone?  This can't be a rare problem.  I suspect if I was back on Gentoo this is something that would be fixable.  Anyone else out there familiar with how the consoles work in Ubuntu's kernel and what the problem here might be?

---

### Post by georgelenzer on 2013-02-22
I made some progress although it was unexpected.  I decided to experiment with the Nouveau driver.  Given that Nouveau is an Xorg driver, I didn't think it would solve my problem with the console.  But as soon as I loaded the nouveau kernel module, my console flickered for a few seconds and then... I had it showing on both screens.

Bringing up the X session with 'service lightdm start' (I'd stopped it earlier) now showed me mirrored displays on both the laptop monitor and the monitor attached to the VGA out.  To get this to work solidly required that I remove the proprietary nvidia driver.

I used xrandr and later the ARandr GUI application to control the configuration of my displays.  They default to 4:3 resolutions when both of my screens are 16:9, but this was easily remedied with ARandr.  It also allowed me to simply and visually represent the physical layout of my monitor and laptop.

The only issues remaining are setting up the laptop so that only the external monitor is in use (as I said the internal one has some kind of problem) and that the HDMI port while recognized by Xranrd will not send any signal to the monitors I've tried to use.  I also tried a suspend and resume as someone else had to do that to get nouveau to output to their HDMI device.

Booting up with the HDMI screen connected didn't help either.  Solving these two issues should make my system usable again.  According to the nouveau project Wiki, my GPU (a G96 aka 9600 M GT) should support HDMI.  The HDMI port works fine with the NVidia proprietary driver.  Anyone else familiar with this nouveau issue?

---

### Post by georgelenzer on 2013-02-24
While the NVidia driver works fine for X, it does nothing for the virtual console.  It seems that the only way to get the virtual console displaying on external monitors on my laptop (HP HDX16) is to use Nouveau.  I still think there might be some combination of fbdev/VESA drivers for console that would work, but given that things are no longer as simple as they used to be with Linux 2.x and LILO or Grub 1.x, I'm having trouble figuring out what piece controls what video display outputs the console has access to.  If I have any further revelations, I will update here.  Otherwise I await an answer from someone with more knowledge than I.

---

