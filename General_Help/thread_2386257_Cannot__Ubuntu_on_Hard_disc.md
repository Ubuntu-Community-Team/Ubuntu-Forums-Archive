---
title: "Cannot ??? Ubuntu on Hard disc"
date: 2018-03-02
forum: General Help
---

### Post by nexus77 on 2018-03-02
I have been trying to install Ubuntu on my hard disc  (Acer Aspire E11).
With the Ubuntu USB stick fitted, it loads to 'GNE Grub', where I choose "try Ubuntu  etc".  This works perfectly, but is running from the USB.
Trying to load without the USB stick fitted gives me 'no bootable device'.
I have hunted all over web forums etc, tried modifying the BIOS etc  - enable UEFI, secure boot disabled, enable F12, supervisor password, enable 'trust'  etc etc.
But nothing works.
Any help will be greatly appreciated.
Regards
Mike

---

### Post by oldfred on 2018-03-02
Post this just to see if installed normally.
 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

But almost all Acer need the "trust" set correctly to work.
And some need UEFI updated from Acer to allow trust settings.
Some also have had issues with 17.10 that now are fixed in 17.10.1. Are you using newest or even 16.04.4 which also is new?

---

