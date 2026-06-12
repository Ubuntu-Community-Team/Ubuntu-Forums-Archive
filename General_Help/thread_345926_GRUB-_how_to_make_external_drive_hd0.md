---
title: "GRUB- how to make external drive hd0??"
date: 2007-01-24
forum: General Help
---

### Post by presbp on 2007-01-24
PLEASE DON'T JUST LOOK AT THIS POST AND NOT HELP--PLEASE HELP

in the Ubuntu live CD when I go to install Ubuntu sees my drives as sda for the internal drive which Windows is on and sdb for the external drive.  I partitioned the external drive and installed Ubuntu to the external and the screen where it asks where GRUB should be installed the default is (hd0)  I set it to (hd1) because in my BIOS settings the USB drive is the 2nd drive.  When I switch the drives so that the external harddrive boots first and it runs grub it gives me error 17.  I think that this error has something to do that GRUB is told to boot from the 2nd harddrive but to allow grub to boot I switch the drives in the BIOS so grub is trying to load off of the internal drive.

       I am in the Ubuntu Live Cd right now and before I loaded the live cd I set my USB external drive as my first harddrive in my BIOS.  What I am thinking I can do is tell Ubuntu to install to sdb (the external harddrive as recognized by Ubuntu) **and then tell GRUB to install to (hd0) because the first harddrive in the BIOS now is the external drive.   Will this install Ubuntu and GRUB to the external harddrive if I have the external drive setup as the 1st harddrive in the BIOS and I tell Ubuntu to install to sdb and GRUB to install to hd0?**

_**Thanks for your help**_.  I thought I had seen a problem where GRUB didn't recognize the drives right if they got switched in the BIOS and I was hoping I could fix it this way.

---

