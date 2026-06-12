---
title: "opinions for converting win 7 on hp desktops to ubuntu"
date: 2017-08-10
forum: General Help
---

### Post by seekertom on 2017-08-10
Looking for some educated opinions on best way to proceed.
I have several hp prodesk pcs, about 2 years old, running win 7 pro. I want to move to ubuntu using fresh hd to replace existing hd which will be left intact in pcs. but not used.
I am concerned about changes by hp hardware/firmware that may make my new set ups different from what I am used to, things like uefi, for example.

So, will I be able to simply install a new internal hd in the pc, then just run the live ubuntu cd and be able to set up the hd and new os with out going into overstress mode?

Unless you folks have a better idea...
(not to bash, but we all know how tiresome it is to constantly have to deal with brand 'm'... that's why the change. :D  )
thanks, st ):P

---

### Post by oldfred on 2017-08-10
If you have a two year old system, it probably is UEFI.
But most Windows 7 installs are BIOS/MBR.

How you boot Ubuntu installer flash drive UEFI or BIOS is then how it installs.
HP is not particularly friendly with anything other than Windows and specifically violates UEFI standard. It uses description as part of UEFI boot and only valid description is "Windows Boot Manager". But there are multiple work arounds, which is best for you depends somewhat on configuration.

Do you want UEFI or BIOS install?
You can with Ubuntu use gpt partitioning and if you have both the ESP - efi system partition (for UEFI) and a bios_grub partition (for BIOS boot) you can install and then easily later switch boot modes. If you install with BIOS and MBR partitioning, you usually have to totally redo drive, although there are some ways to convert.

       [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
[/URL]
 UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 
      
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

See also link in my signature.
 [URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by seekertom on 2017-08-23
Thanks. I did my install from a live cd, but to a new hd, not the original. I need to keep orig intact for later purposes. Cant hook up two drives to this hppc unless add-in board and dont want to do that. So, I installed to new hd leaving original hd disconnected. I took all defaults and its working fine. Thanks for the confidence boost.
One remaining question (only one??? ya..) is there a definitive way to determine what situation is presently involved in any pc, win, ubie etc, re efi, bios etc?
thanks, st

---

### Post by oldfred on 2017-08-23
I like to document boot configuration with Boot-Repair's summary report:

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

You can also list hardware with many commands. One of them:

 sudo lshw

---

