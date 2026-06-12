---
title: "Upgrade to 14.04 failed"
date: 2014-10-02
forum: General Help
---

### Post by onipar on 2014-10-02
Hi all,

My dad runs Ubuntu (I built his computer for him), and he updated to 14.04 LTS last night.  He called me today because as he put it "everything is gone!"

The computer loads to the sign in screen, and it even allows him to sign in, but the desktop is just a blank 14.01 LTS page with nothing on it.  No task bars, no icons, NOTHING.  

The arrow is there, and it moves, but does nothing when right clicked.  

I tried booting into bios, but for some reason that's not working either.

I'm TOTALLY out of my depth here and haven't the foggiest notion of where to even begin.  Please help.

---

### Post by grahammechanical on 2014-10-02
Do you get a Grub boot menu? If Ubuntu is the only OS on the machine then you will not see a boot menu. So, press Shift as the machine boots. That should bring up the Grub boot menu. Select Advance Options for Ubuntu and open its sub-menu and then select Recovery mode. At the Recovery menu select Resume. That may load to a login screen and then to working desktop using am open source video driver as a fall back video driver.

If you get that far, then go to System Settings>Software and Updates>Additional Drivers tab. Allow the utility time to find video drivers (internet connection needed) and try a different video driver.

Regards.

---

### Post by onipar on 2014-10-02
What does the grub boot menu look like?  My parents have two different sign on names, so when it starts up, it goes to the login screen.  

I tried pressing shift as it boots up, but that didn't do anything...  Tried a few times, pressing it at different intervals and whatnot, but there was no change, it just would go straight to the login screen.

---

### Post by onipar on 2014-10-02
Duplicate replay, sorry.

---

### Post by onipar on 2014-10-03
Any ideas?  Kinda desperate, thanks!

---

### Post by oldfred on 2014-10-03
You mentioned blank screen and right click (not left click?). I had that with one of my installs, and right click opened a change desktop screen & I could click on system settings and install the proprietary nVidia driver from System Settings, Software & Updates, drivers tab.

Normally I have to use nomodeset from grub menu to get into low quality graphics as I have nVidia card.
What video system is this?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by onipar on 2014-10-03
I think it must be a graphics/video driver error because it says running in low graphics mode, but no matter what selections I try through recovery, I can't get to a working desktop.

---

### Post by QIII on 2014-10-03
It would be very helpful if you would tell us about your graphics adapter.

:)

---

### Post by onipar on 2014-10-03
[COLOR=#333333][FONT=Ubuntu]I built the computer for him a couple years ago. It's an AMD system ( Gigabyte 880gma-usb3, AMD phenom II X3, 1 T Hdd, 8 GB G skills Ram).  The board has [/FONT][/COLOR]
[LIST]
[*]Integrated ATI Radeon HD 4250 graphics (DirectX10.1).  Thanks for the help :-)
[/LIST]

---

### Post by oldfred on 2014-10-03
I do not know AMD, but have seen that only 5000 or newer are still supported. You have to install a legacy driver for the older AMD or use the open source driver which may not fully work.

Have you tried nomodeset?

Not sure if this has been updated or not? Standard fglrx only supports newer cards/chips.
 This repository provides AMD Catalyst drivers for legacy graphics Radeon HD 2xxx - 4xxx for several versions of Ubuntu.
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

---

### Post by onipar on 2014-10-03
Much of the page you linked is Greek to me (I really don't use ubuntu often).  Is there an easy terminal code I can paste in that will add the drivers needed?

EDIT:  No, I don't know what [COLOR=#000000]nomodeset is...[/COLOR]

---

### Post by onipar on 2014-10-03
I uninstalled the fglrx driver and installed the open source driver.  That fixed it.

---

