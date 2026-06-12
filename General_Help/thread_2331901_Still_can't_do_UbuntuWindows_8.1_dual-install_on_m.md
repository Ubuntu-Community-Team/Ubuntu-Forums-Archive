---
title: "Still can't do Ubuntu/Windows 8.1 dual-install on my hp15"
date: 2016-07-26
forum: General Help
---

### Post by t0p on 2016-07-26
I thought maybe waiting would bring me to a place where Ubuntu and Windows 8.1 would play together nicely on my hp15 (15-g261-sa) but over 12 months later and it still won't do it.

Anyone out there know of a way (remembering that 10+ years of Ubuntuinh has most definitely not made me a guru - I'm not scared of the cli, but nothing I have found and tried so far has not worked...).

Alternatively: can anyone suggest an inexpensive available-in-the-uk laptop will  allow the dual-boot?  I'm poor, so it's gotta be cheap.  And I'm in the UK. so it's gotta be an in-UK solution.

Thanks all!

---

### Post by yancek on 2016-07-26
HP and a few other manufacturers violate the UEFI standards making it more difficult to use anything but windows.  I don't use UEFI mysel so can't help but I have seen quite a number of posts dealing specifically with UEFI dual-boot for HP here at the forums.  You might try using the search function here while you wait for someone to respond.

---

### Post by oldfred on 2016-07-26
Just about every model HP needs a work around. Most if dual booting make the fallback or hard drive boot entry really be shim. That is copy shim to /EFI/Boot as bootx64.efi and boot hard drive UEFI entry.
Boot-Repair now automatically does that:
 
 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.
'Use the standard EFI file' in advanced options. 
       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Similar info in link in my signature:
      Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair) 
    
 [http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook](http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook)
Some HP will not boot a flash drive that is gpt partitioned.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260)
HP Check if Customized UEFI settings available like this  HP ProBook 4340
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)
HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)
Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 Details
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244)

---

### Post by tea for one on 2016-07-26
> **t0p said:**
> I thought maybe waiting would bring me to a place where Ubuntu and Windows 8.1 would play together nicely on my hp15 (15-g261-sa) but over 12 months later and it still won't do it.

Anyone out there know of a way (remembering that 10+ years of Ubuntuinh has most definitely not made me a guru - I'm not scared of the cli, but nothing I have found and tried so far has not worked...).

Alternatively: can anyone suggest an inexpensive available-in-the-uk laptop will  allow the dual-boot?  I'm poor, so it's gotta be cheap.  And I'm in the UK. so it's gotta be an in-UK solution.

Thanks all!

Good evening

I recently purchased an HP Stream 11.6 netbook style laptop which arrived via a well known supermarket chain in the UK for £149.00 inc VAT.

I originally intended to remove Widows 10 completely and install Xubuntu Core, however, I changed my mind and thought I would experiment with a dual boot and muck around with the HP UEFI bios incarnation. The UEFI bios is like a mini OS, plenty of switches to toggle and alternatives to try.

This was my first look at a UEFI system and it is a bit daunting.

I managed to boot a live USB after about 90 minutes fiddling with the UEFI settings and it took three atttempts to successfullly install to the hard drive.

My main obstacle was "grub-efi amd64 signed package failed to install"

I got round this eventually by turning off the secure boot in the UEFI settings and reinstalling. I expected to find that Windows 10 would refuse to load but to my surprise it loaded with secure boot disabled - who really knows how these UEFI devices function?

Although this netbook has only 32GB hard drive, I've managed to leave Windows 10 intact together with the Windows recovery partition and installed Xubuntu Core (+ Qupzilla, Parole media player, Synaptic, Mousepad and Xubuntu Restricted Extras and a few small utilities)

Secure boot is disabled and legacy boot is enabled and both Xubuntu Core and Windows 10 boot and function adequately. Xubuntu is a bit quicker but this only reflects my unfamiliarity with Windows 10.

When I turn the power on, grub does not appear automagically like a pre UEFI machine, I have to press F9 to choose the boot device and then grub will appear (depending on you personal grub configuration settings). If I do not press F9, Windows 10 will load due to some priority(?) bulit into the UEFI by HP.

Anyway, my first question for the OP is:-

Have you managed to boot a live DVD/USB on your laptop?

Kind regards

---

### Post by gordintoronto on 2016-07-27
t0p, "it won't do it" doesn't give people anything to work with. If you say, "I did A and B and expected result X, but Y happened instead," we might be able to help.

For example, did you shrink the a partition to make space for Ubuntu? Did you boot from a DVD?

I have an HP laptop which happily multi-boots Windows 10, Xubuntu 16.04 and Linux Mint 18 64-bit Mate, but it's pre-UEFI. The only issue I had with it was that the goofs at HP used all four MBR primary partitions.

---

