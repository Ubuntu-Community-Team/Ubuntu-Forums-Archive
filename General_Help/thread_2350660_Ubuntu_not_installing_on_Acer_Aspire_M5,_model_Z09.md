---
title: "Ubuntu not installing on Acer Aspire M5, model: Z09."
date: 2017-01-26
forum: General Help
---

### Post by uborba on 2017-01-26
Hi, I'm trying to install Ubuntu on my Ultrabook Acer Aspire M5, model no.: Z09.

Boot works from USB, I tried various versions so far, yesterday I tried the last desktop version 16.10.
I have USB medias for various versions, they all boot fine, but it fails to install on HDD(500GB) and also on internal SD card(20GB).
I don't have Windows installed, HDD is formatted, I also used GParted to verify bad blocks, but there's nothing wrong.
Yesterday I installed 16.10 and installation finished, then I removed Bootable USB pen drive and rebooted the system, the message is "no boot found". Looking on BIOS and the HDD is configured as first boot option.
Seems like I'm forgetting something, there are options on BIOS to boot like Legacy or EFI, or something and I don't know what this means. 
I was also searching Google about it, nothing specific to this model, there are workarounds for dual boot with grub, but I don't have Windows anymore, I don't care about Windows anyway, won't try to reinstall it, also I had serious performance problems when I was using Windows.

I'm stuck, don't know if there's a possibility that Ubuntu doesn't support this model, or the BIOS, or if I need to install another Linux version.
I need help, any other Linux version with good interface is good, I was trying Ubuntu because I like it.

---

### Post by oldfred on 2017-01-26
You need to understand & know UEFI from BIOS.
If not dual booting with Windows you can use either UEFI or BIOS, but some slight advantages to UEFI. And advantages to gpt partitioning which is the default with UEFI, but Ubuntu can boot from a gpt partitioned drive with either UEFI or BIOS if correct supporting partitions are on drive. 

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

But Acer is the only vendor that in UEFI boot mode requires you to set a supervisory password and enable "trust" from with in UEFI to the .efi boot files in the ESP - efi system partition.

Also some older threads, mention downgrading UEFI from Acer to older version to get it to work. But newer threads say newest UEFI from Acer works. So just make sure you have newest UEFI from Acer.

 Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 

       Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

### Post by uborba on 2017-01-26
Thanks, this is a lot to study and understand, wish it were easy.
I was reading articles from Ubuntu help site, then I start over again, this time flowing here: 
[https://www.ubuntu.com/download/desktop/install-ubuntu-desktop](https://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Then it generated this log, but still no boot. I'm not aware with log info, was looking and there's still info about Windows system and it seems also, there's a Grub: 
[http://paste2.org/y0UywKDx](http://paste2.org/y0UywKDx)

About system/BIOS administrator "trust?", it's still on default "frozen" password.
For now I have a lot to read and understand with your response. Thanks, will work hard tonight.

---

### Post by oldfred on 2017-01-26
It looks like your install did not have a Ubuntu boot entry in UEFI.
But Boot-Repair's run of grub install then grub installed a new UEFI boot entry.

Now you need to set the UEFI supervisory password & then set trust on /EFI/ubuntu/shimx64.efi.

---

### Post by uborba on 2017-01-26
Verified about BIOS version: 
Available BIOS, 2.22(2013) is installed. 
There are three images:
[https://imgur.com/gallery/BRLEM](https://imgur.com/gallery/BRLEM)

But latest BIOS is 1.15
V 2.16 is for Windows
V 2.22 is for Windows
V 1.15 isn't system specific.

Should I update to 1.15 since it's latest version looking release date?

---

### Post by oldfred on 2017-01-26
Normally the Windows versions work as most dual boot.
So your 2.22 should be ok. 

Is 2013 last update?
Both Linux UEFI and vendors UEFI back in 2013 had bugs that since have been fixed.

---

### Post by uborba on 2017-01-26
Available BIOS dates:
v2.16: 03/2013;
v2.22: 06/2013;
v1.15: 01/2014.

The lower version number is last released version, I'm confused, but there's more about it, versions 2.xx are for Windows. Latest version is 1.15 and isn't system specific, look the images: [https://m.imgur.com/gallery/BRLEM](https://m.imgur.com/gallery/BRLEM)

---

### Post by oldfred on 2017-01-26
Do not know.
I have always had good luck updating BIOS, but some have said not to change it unless the updates fix something specific that you have issues with.

Do not know then what to suggest.

---

