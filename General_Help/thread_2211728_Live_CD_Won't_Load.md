---
title: "Live CD Won't Load"
date: 2014-03-17
forum: General Help
---

### Post by Unanimated on 2014-03-17
Hi, a couple of nights ago I bought one of those $300 unnamed HP laptops with Windows 8 preinstalled. While it isn't exactly bad at running Windows 8, I know it'll be able to run Ubuntu better - plus, Windows 8 is Windows 8. I downloaded the .iso (64-bit) just fine and burned it to a DVD, and I also changed the BIOS/UEFI settings to boot from CD/DVD and I disabled secure boot. As far as I can tell, there are no other settings in the BIOS of this laptop that would affect booting, but I could easily be wrong. The problem I have is with loading the live CD. The Ubuntu logo will show up just fine, and it'll appear to load everything, and once it seems like it's right about to get into the desktop (a bunch of lines of code show up with what's happening behind the splash screen, no failures display, and it goes away after a few seconds), the CD drive slows down, eventually stops, and the screen turns blank and stays that way. I used the utility to check the DVD for errors and it didn't find any. The same thing happens when I select "install" instead of live CD. I've checked around the internet, but what seems to work for other people is to change or disable settings within BIOS that this laptop doesn't have. For specifics, it's an HP 15-g019wm. Any help would be much appreciated.

---

### Post by Impavidus on 2014-03-17
Maybe the live disk just doesn't like the graphics card &#8211; or vice versa. Does it have nvidia graphics? Try the nomodeset boot option. [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132), scroll do[SIZE=2]wn to "How to enable kernel options on the livecd (before install)[/SIZE]".

---

### Post by Unanimated on 2014-03-17
I'll try that later tonight - it has integrated AMD graphics. Would that raise difficulties upon a full installation?

---

