---
title: "Dell XPS 13 (Ivy Bridge) problem - flickering screen with intel Xorg driver"
date: 2013-11-17
forum: General Help
---

### Post by ayqazi on 2013-11-17
Hello,

I have posted this on askubuntu.com, but thought I'd repost it here for more coverage.  [The askubuntu.com post is here: http://askubuntu.com/questions/378002/flickering-screen-with-kubuntu-13-10-on-xps-13-ivy-bridge]("http://askubuntu.com/questions/378002/flickering-screen-with-kubuntu-13-10-on-xps-13-ivy-bridge") (if you reply there, please post a simple message saying you have done so to keep this thread nice and bumped up).


I installed Kubuntu 13.10 on an XPS 13 early 2013 model (L322X), having had to pass the 'nomodeset' parameter to the installer. Strangely, I only had to do this after I updated the Windows installation to 8.1.

Without nomodeset, and using the 'intel' Xorg driver, both the installer screen and the login screen of the actual OS look something like old CRT monitors would show images if you passed in an unsupported refresh rate.

This is a really bad video of how it looks: [http://www.youtube.com/watch?v=r4jxAfLTaT4](http://www.youtube.com/watch?v=r4jxAfLTaT4) . Sorry for the lack of quality.

Now, in the installed OS itself, if I boot with 'nomodeset' and use the 'fbdev' driver, I can get Xorg to work. However, this isn't optimal of course.

What's happening? As I said, the installer only started doing this without 'nomodeset' after I updated the Windows partition to Windows 8.1.

Also, if the intel driver is used with 'nomodeset', this error appears:

```
[     4.224]    ABI class: X.Org Video Driver, version 14.1
[     4.224] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
        i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
        915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
        Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
        GM45, 4 Series, G45/G43, Q45/Q43, G41, B43, HD Graphics,
        HD Graphics 2000, HD Graphics 3000, HD Graphics 2500,
        HD Graphics 4000, HD Graphics P4000, HD Graphics 4600,
        HD Graphics 5000, HD Graphics P4600/P4700, Iris(TM) Graphics 5100,
        HD Graphics 4400, HD Graphics 4200, Iris(TM) Pro Graphics 5200
[     4.225] (II) VESA: driver for VESA chipsets: vesa
[     4.225] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     4.225] (II) FBDEV: driver for framebuffer: fbdev
[     4.225] (++) using VT number 7

[     4.228] (WW) Falling back to old probe method for modesetting
[     4.228] (EE) open /dev/dri/card0: No such file or directory

```
Help?

Thanks

---

### Post by oldfred on 2013-11-17
Is it booting with the Intel Video, or does it have dual video?

Not sure but others have posted these as options, may vary by Intel chip model.
 Some other Intel boot options
acpi_osi=Linux  acpi_backlight=vendor
      
  i915.i915_enable_rc6=1

 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

      
 Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)

 Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)

Someone posted that all the features of Sputnik are in 13.10.

---

### Post by ayqazi on 2013-11-17
Hello,

Nothing in that post worked, sorry.  There is only 1 video chip in there, the intel one.

I'm using 13.10 - Saucy - not 12.10.  As I said, things seemed to work until I upgraded the Windows partition to 8.1.

Sorry - anyone else got any ideas?

Thanks

---

