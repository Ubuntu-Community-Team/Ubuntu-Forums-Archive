---
title: "Broken dual boot 8.1 &amp; Kubuntu"
date: 2015-08-27
forum: General Help
---

### Post by makem2 on 2015-08-27
I did have a working dual boot kubuntu but for some reason I now cannot boot either OS.

I have a live usb of kubuntu but cannot boot from this. I think that is caused by 'fast boot' or 'uefi' boot which the machine has.

I am unable to turn off the ufi from the machine bios setup as it is greyed out.

Where I am at the moment:

GNU Grub version 2.02~beta2-9ubuntu1

Minimal bash-like line editing supported. for the first word TAB etc............

Any help would be appreciated as I have a totally dead machine as far as I am concerned.

---

### Post by oldfred on 2015-08-27
Some systems when you have Secure boot on, must specify that you allow booting from any other device. Check for additional settings. Some like Acer require a password to enable those extra settings.
 Either turn secure boot off in UEFI, but if your installs are booting in UEFI mode be sure to boot flash drive in UEFI mode, not BIOS mode.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by makem2 on 2015-08-27
The usb has been booting correctly for several installs while i test flavors.

I do not have any other options in bios.

Is there any command from where I am now which would help?

When I try 'help' I get a fast scrolling list half of which I cannot see.

---

### Post by makem2 on 2015-08-27
I had another look at bios setup and found 'security. via that I was able to turn of uefi and fastboot to get a CSM boot whatever that is.

The usb booted and I am 'trying kubuntu'. still not sure where to go from there but a good start.

Thank you for you suggestions.

---

### Post by Vladlenin5000 on 2015-08-27
> **makem2 said:**
> The usb booted and I am 'trying kubuntu'. still not sure where to go from there but a good start.

No, not really. That just means your flash drive don't support UEFI. Depending on the method/tool used that may occur.

Now...
If your dual boot was working before, and assuming a factory installed Windows 8.1, then both installations - Windows and KUbuntu - are in UEFI mode (as they should be). _By turning CSM (legacy BIOS) on, now it's guaranteed you won't be able to boot neither_.

---

### Post by makem2 on 2015-08-27
Got a boot configuration error when booting after adding windows to the grub file.

I think it said boot/BCD file missing.
sda1 ntfs winRE
sda2 fat32 boot
sda4 ntfs Win 8.1
sda5 ntfs Data
sda6 ntfs recovery
sda7 ext4 /
sda8 linux swap
sda9 ext4 home

I used:

set root=(hd0,4) in the script to repair grub

---

### Post by oldfred on 2015-08-27
Your Windows is only UEFI, it will not work in BIOS/CSMLegacy mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

You need to have CSM off. UEFI on, and probably Secure boot off.
From UEFI boot tab's menu, you should have two entries for any flavor Ubuntu live installer. One is UEFI and the other CSM/BIOS.

---

### Post by makem2 on 2015-08-28
> **oldfred said:**
> Your Windows is only UEFI, it will not work in BIOS/CSMLegacy mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

You need to have CSM off. UEFI on, and probably Secure boot off.
From UEFI boot tab's menu, you should have two entries for any flavor Ubuntu live installer. One is UEFI and the other CSM/BIOS.

I have booted with UEFI on and Secure boot off.

As the kubuntu install is fresh and /home is on a separate partition, can I not now reinstall a new copy in the partitions which already exist and this will create a new grub which includes windows?

---

### Post by makem2 on 2015-08-28
Well, I took a chance!

It worked and everything appeared normal and working a susual until an update then things messed up.

[http://ubuntuforums.org/showthread.php?t=2292470&p=13346236#post13346236](http://ubuntuforums.org/showthread.php?t=2292470&p=13346236#post13346236)

---

