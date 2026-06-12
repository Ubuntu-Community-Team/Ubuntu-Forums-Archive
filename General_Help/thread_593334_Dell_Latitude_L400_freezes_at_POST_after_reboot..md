---
title: "Dell Latitude L400 freezes at POST after reboot."
date: 2007-10-27
forum: General Help
---

### Post by OpticalIllusion on 2007-10-27
I'm running Xubuntu 7.10 on my Dell Latitude L400.  Most things are working fine so far.  Even Suspend, Hibernate, and Shutdown all work just fine.  But, every single time I reboot, it will completely lock up on the POST screen.  I turned on the feature that shows you what the POST is testing and evidently it's freezing right after detecting the hard drive.

I had Windows XP on this computer before and never had an issue with rebooting.

How can I fix this or even see what's going on?

---

### Post by OpticalIllusion on 2007-10-27
bump

---

### Post by OpticalIllusion on 2007-10-28
Well, the only thing I have figured out is for some reason it feezes when it's plugged into AC power, but not on battery.  I messed with a few BIOS settings with no luck, but I feel is the OS because, like I said, Windows XP worked just fine.

---

### Post by kubapet on 2007-11-17
Hi,
I have the same notebook running gentoo and I have had the same problem, but now it works fine.
I' ve just recompiled DSDT for ACPI.

read this and try this: [http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php)

you need to download DSDT file for latitude l400 and put it to /etc/mkinitramfs/DSDT.aml. Then run "sudo dpkg-reconfigure linux-image-$(uname -r)"

---

### Post by Pollmak on 2007-11-22
Hey man i have the same L400 and have noticed the same/similar issues with boot up boot up. i will tested the sugested post and report my findings (lol that sounds soo geeky man!:lolflag:)

---

