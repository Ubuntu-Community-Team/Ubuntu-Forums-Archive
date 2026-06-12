---
title: "Where Do I Find and Install Graphics Card Drivers?"
date: 2013-08-01
forum: General Help
---

### Post by shabalabadingdong on 2013-08-01
Ubuntu has been slow, on my computer (which is reasonable because my computer is about 7 years old now), but when I mean slow, I mean really slow.  It will take very long to do things, like search, open and close apps, and more.  I have to install other desktop environments like LXDE, and GNOME to make the OS run faster and more snappy.  But I don't really like these desktop environments all that much, I like Unity, it's great and my favorite.  I think it's the graphics card drivers that boost performance, but I cannot seem to find them, they aren't under the Additional Drivers tab, and I search online and cannot find them.  I want to try to get Ubuntu to run better, I have tried preload, installing linux kernel 3.10.1, disabled all effects with Compiz, decreasing the swappiness value to 5, and things seem to be better but not too much.  I think I need more RAM I have about 870 MB.


My Graphics Card is **Gallium 0.4 on ATI RS690**


**-Thanks for any help!**

---

### Post by DeathByDenim on 2013-08-01
According to [Wikipedia]("https://en.wikipedia.org/wiki/AMD_690_chipset_series"), the RS690 chipset belongs to the Radeon Xpress 1200 series. And according to AMD, those have been moved to legacy support. See [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)
This means that you need to use (at most) the 9.3 Catalyst drivers to get support for that card.
It's strange that it doesn't show up under Additional Drivers, but assuming you use Ubuntu 12.04, you should be able to manually install it if you install the package fglrx from the Software Centre. I believe that provides version 8.960. You can also try fglrx-updates, which provides version 9.000 or fglrx-experimental-9, which provides version 9.010.

And yeah, more RAM would most likely help you.

---

### Post by QIII on 2013-08-01
Hello!

Unfortunately, even if you install that driver that would theoretically work with that card, the driver will not work with any version of X Server post 2009.

And if you were to try any of the (highly unrecommended -- I've had to bail a couple of users out) methods to get the HD 2000 - HD 4000 cards to work, you would still be left with an X Server version too new to work with that card.

I'm afraid the open source Radeon driver is all that will work.  There really is no other option.

You might try something like Bodhi Linux (which is based on a stripped down Ubuntu 12.04 and uses the Ubuntu 12.04 repos), which, instead of a DE, uses Enlightenment 17 -- a very light graphical desktop shell.

Best wishes!

---

### Post by DeathByDenim on 2013-08-01
Ah, you're right. I missed the fact that 12.04 has Xorg 7.6 and the driver from the AMD page only supports up to 7.4...
Well, that explains why it wasn't in the Additional Driver section.

---

### Post by shabalabadingdong on 2013-08-01
> **DeathByDenim said:**
> Ah, you're right. I missed the fact that 12.04 has Xorg 7.6 and the driver from the AMD page only supports up to 7.4...
Well, that explains why it wasn't in the Additional Driver section. Thank you all very much.

---

### Post by MIJ-VI on 2013-08-01
**Plan B** for more speed and possible ATI graphics support for an older PC; Try Linux Mint 13 MATE (MATE is a contemporary fork of the old Gnome 2.3.x UI formerly used in Ubuntu circa version 9.10):

Xorg info from Linux Mint MATE 13, 64 bit:

```
john@john ~ $ Xorg -version

X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
Current Operating System: Linux john 3.2.0-51-lowlatency #53-Ubuntu SMP PREEMPT Fri Jul 26 14:18:10 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-51-lowlatency root=UUID=d7cb18ed-3fd2-4576-8bab-966abe4ea738 ro quiet splash vt.handoff=7
Build Date: 05 April 2012  04:32:37AM
xorg-server 2:1.11.4-0ubuntu10 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.24.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
john@john ~ $ 

```

And get more RAM. One source of affordable components for older PCs:

Free Geek at DuckDuckGo
[https://duckduckgo.com/?q=Free+Geek](https://duckduckgo.com/?q=Free+Geek)

---

