---
title: "A USB that refuses to be recognized in Ubuntu 16.04"
date: 2020-09-04
forum: General Help
---

### Post by andysharpie on 2020-09-04
Hello all. I have here a USB which I have made into a live boot. However, when I tried on use it, the PC I am trying to upgrade did not recognize the drive or ask me what to do with it. I eliminated the obvious causes; no dead USB ports, nothing to do with the system, which is Ubuntu 12.04 ( I rebooted a couple of times to check.) I eliminated the possibility of a dead USB stick by creating another one and testing it. My system did not recognize the second stick either. I checked it on Windows 10, and it was recognized. I reformatted the drive (which Windows wanted me to do anyway), went back to my primary computer, and created the live boot again. I unplugged the drive and inserted it, but to no avail. I went through this process multiple times, changing the only variables I could think of. In all, the issue is not one of the following: a bad USB stick, a corrupted ISO file, the application used to create the live boot (I used Startup Disk Creator and BalenaEtcher), or faulty USB ports on either my computer or the one I am updating. Everything works fine with a freshly formatted drive, but as soon as I finish making a live boot, Ubuntu is blind to its presence, and therefore cannot boot from it at startup.
I've come to the end of my bag of tricks, and am sorely tempted to say there's a ghost haunting my electronics ;P
Any advice is greatly appreciated.

--Andy

---

### Post by guiverc on 2020-09-04
Ubuntu 12.04 LTS is years past it's *End-of-Life*.

The obvious checks are is the ISO is corrupted ([https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)) which you claim to have performed, then the write to install media ([https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck))

If I can't perform the media validation checks on one box, I usually walk it (thumb-drive with installed ISO media) to another box and check it there.  If it fails on the second box, I assume it's an invalid ISO or corrupted write to install media (most of the time it's the latter, ie. bad write to media).

If it's a *daily* or *released for testing* ISO, I'll test on a very different box (eg. if first two here uEFI & secure uEFI, my third test will be on BIOS).  However with 12.04 media; your ISO is so old it may not boot on any secure uEFI machine (esp. with updated dbx database).

---

### Post by Impavidus on 2020-09-05
If I get this straight, you've got a computer with an obsolete Ubuntu release and you want to install a supported release. You created a live disk and try to boot using that live disk, but fail.

A few things to consider:
Whether your obsolete Ubuntu can read the live disk is irrelevant. The important thing is that your bios/uefi can read it, so you can boot.
When coming from an unsupported release of Ubuntu, I would not attempt any type of upgrade other than a fresh install. Backup any files you want to keep and format the partitions.
What release of Ubuntu are you trying to install? It's probably best to jump straight to 20.04.
Does your computer use legacy mode/bios of uefi? Legacy mode (which is uefi emulating bios) wouldn't be unexpected on a computer running 12.04. Some live disk creation tools create live disks that only work in one mode.
When entering the uefi/bios of your computer, does it give you the option to boot from usb? If so, and you try, what happens?

---

### Post by HermanAB on 2020-09-05
First of all, the Ubuntu install ISO file is a complete file system.  You don't need to format the USB stick, or run any special software to prepare it for writing to the USB stick.  All that you need to do is write it exactly as is to the USB stick.

On a Windows machine, you can do that with *rawrite* and on a Linux machine, you can do that with *dd* or *cat*.

---

### Post by andysharpie on 2020-09-06
> However with 12.04 media; your ISO is so old it may not boot on any secure uEFI machine (esp. with updated dbx database).

--- To be clear, the ISO I'm working with is Linux Lite 3.8 32-bit. How do I investigate a bad write-to-media?

> If I get this straight, you've got a computer with an obsolete Ubuntu  release and you want to install a supported release. You created a live  disk and try to boot using that live disk, but fail.

A few things to consider:
Whether your obsolete Ubuntu can read the live disk is irrelevant. The  important thing is that your bios/uefi can read it, so you can boot.
When coming from an unsupported release of Ubuntu, I would not attempt  any type of upgrade other than a fresh install. Backup any files you  want to keep and format the partitions.
What release of Ubuntu are you trying to install? It's probably best to jump straight to 20.04.
Does your computer use legacy mode/bios of uefi? Legacy mode (which is  uefi emulating bios) wouldn't be unexpected on a computer running 12.04.  Some live disk creation tools create live disks that only work in one  mode.
When entering the uefi/bios of your computer, does it give you the option to boot from usb? If so, and you try, what happens?

--- You have summed up the situation well. I would gladly go straight to Ubuntu 20, but this box is 32-bit only, and it's at least 13 years old, probably more. Its only upside is that it has barely been used. When I first tried to boot from the live USB, I went into the BIOS settings (it is definitely using BIOS) and set the boot priority order to USB first, HDD second. BIOS did not see the USB and booted straight from Ubuntu 12 every time. I'm sorry I failed to articulate that previously.

Thanks.

---

### Post by guiverc on 2020-09-06
Linux Lite is not Ubuntu, nor *flavor* of Ubuntu thus I have no idea; but I'd assume its like the link I already provided (it applied to all Ubuntu and *flavor* ISOs up to and including 19.10)

I used machines as old as from 2003, including pentium M, pentium 4, pentium D etc. in testing Lubuntu & Xubuntu releases up to and including 19.04, when x86 or 32-bit ISOs were dropped.  (these are older boxes than your 13 year old box; as it includes boxes up to 18 years old)

I continue to use those boxes for testing x86 or 32-bit ISOs, eg. last months 18.04.5 ([http://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](http://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/))

FYI: Are you sure it's 32-bit?  64-bit machines started being produced and sold 2001, though it still took a few years for low-end *consumer* grade machines to move to 64-bit.  Cheap machines were often sold with 32-bit windows (on 64-bit machines) as it reduced the price by $5 and most users didn't understand 32-bit vs 64-bit, but understood $5 cheaper.

---

### Post by mastablasta on 2020-09-07
yes, what is the CPU on the PC?

Also if it really is 32 bit only then you need to start looking at Debian stable or maybe a Debian based OS aimed at low end PC (AntiX, Bunsenlabs, MX Linux...).

---

### Post by andysharpie on 2020-09-09
Ok, so I tried the thumb drive again just to make sure, and, wonder of wonders, the live system finally booted. I do not know to what I can attribute this blessing, but I am very thankful for all your help none the less.

--Andy

---

### Post by mastablasta on 2020-09-10
> **andysharpie said:**
> Ok, so I tried the thumb drive again just to make sure, and, wonder of wonders, the live system finally booted. I do not know to what I can attribute this blessing, but I am very thankful for all your help none the less.

--Andy


you blow down the USB key and then it works. just like game cartridges on those old consoles :)

---

