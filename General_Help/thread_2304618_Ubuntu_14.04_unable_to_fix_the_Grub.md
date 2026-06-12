---
title: "Ubuntu 14.04 unable to fix the Grub"
date: 2015-11-28
forum: General Help
---

### Post by childintime on 2015-11-28
After a lot of struggle I finally installed ubuntu 14.04.03 (The only OS on my computer) but I cannot fix my grub.

Everytime I reboot I get into `grub rescue` prompt. To boot normally I perform this commands:

    ```
grub rescue>  set boot=(hd0,gpt4)
grub rescue>  set prefix=(hd0,gpt4)/boot/grub
grub rescue>  insmod normal  
grub rescue>  normal 
``` 

After booting I tried this:

    ```
sudo update-grub
    sudo grub-install /dev/sda
```

But nothing has changed.

I also tried downloading Boot-repair and doing default repair, but I get an error "grub is still preset, try again later". It also recommends to try boot repair with `separate efi partition` disabled, and then boot repair finished successfully, but grub still not fixed.

Any tips how to fix my grub?

---

### Post by grahammechanical on 2015-11-28
There are a couple of things you can do for us. Tell us about the hardware. Why was installing such a struggle? Please run Boot Repair again and get the URL to the boot info report and post it in your thread.

You have GPT partitioning. That points to a motherboard with a UEFI boot system and not a BIOS boot system. That should not be a problem unless we install Ubuntu in EFI mode and then switch the UEFI boot system to Legacy mode. Or the other way around.

Regards.

P.S. I am wondering why, with Ubuntu as the only OS is Ubuntu installed in the fourth partition on that disk? hd0,gpt4 = first hard disk & fourth partition.

---

### Post by TheFu on 2015-11-28
GPT can work fine with non-UEFI booting. I do it on 3 systems.

Please post the "boot repair" URL so we have all the facts we need.

---

### Post by childintime on 2015-11-28
Thanks guys, well I am really a newbie when it comes to BIOS/UEFI and partitioning stuff.

On this computer I had Windows 8 long time ago, then I had Ubuntu for more than a year, but recently I had to reboot it and got a "kernel panic" error. Couldn't boot with any of the kernels nor into recovery.

Then I tried to install from USB, but in Bios I had two selections for boot priority, I think one of them mentions UEFI. With one of those I couldn't install Ubuntu (got error while installing GRUB), and with another I could.

Finally, my BIOS has absolutely no settings for UEFI and it's old BIOS screen. However [COLOR=#111111][FONT=Consolas]/sys/firmware/efi[/FONT][/COLOR] exists so I guess it's booted into UEFI?

I am using Laptop Asus K56C.

Alright so Boor-repair with default options:

```
"BIOS-Boot detected. You may want to retry after deactivating the [Separate /boot/efi partition:] option. Do you want to continue?"
- Yes
Then I get "GRUB is still present. Please try again."
```

So I disable "separate boot efi partition" option as advised. I get:

```
"EFI detected. You may want to retry after activating the [Separate /boot/efi partition:] option. Do you want to continue?"
- Yes
```
and it completes successfully, but I still boot only into GRUB rescue console. Log: [http://paste.ubuntu.com/13544465/](http://paste.ubuntu.com/13544465/)

---

### Post by TheFu on 2015-11-28
First things first.  ALL PCs that came with Wni8 or later are required (REQUIRED) to have UEFI and use SecureBoot. This was a Microsoft MANDATE.  Often it can be disabled, however, the Linux Foundation strongly recommends against that - using UEFI and SecureBoot help with Linux security too.

I'm in the middle of a failing keyboard replacement on a chromebook C720 today ... already had the dremel out ... so you have an idea how well this is going (stripped a screw and it appears that breaking 50-100 plastic rivets is mandatory to replace the just the $26 keyboard - Acer only sells the $80 "keyboard assembly" .... I'll look to update more on this issue here, if/when that is finished.

---

### Post by childintime on 2015-11-28
> **TheFu said:**
> First things first.  ALL PCs that came with Wni8 or later are required (REQUIRED) to have UEFI and use SecureBoot. This was a Microsoft MANDATE.  Often it can be disabled, however, the Linux Foundation strongly recommends against that - using UEFI and SecureBoot help with Linux security too.

I'm in the middle of a failing keyboard replacement on a chromebook C720 today ... already had the dremel out ... so you have an idea how well this is going (stripped a screw and it appears that breaking 50-100 plastic rivets is mandatory to replace the just the $26 keyboard - Acer only sells the $80 "keyboard assembly" .... I'll look to update more on this issue here, if/when that is finished.

I don't have "secure boot" option in my BIOS though. My BIOS has very little options in general, don't know why.

Ok good luck with that!

---

### Post by yancek on 2015-11-28
What's on the 1TB drive?  The boot repair output shows windows code in the MBR.  You also show Grub code in the MBR of the first drive (750 GB) but you also have an EFI partition with the Ubuntu EFI files.  If you use EFI to boot, you should not have boot code in the MBR.  If you use MBR to boot, you don't need an EFI partition.  The grub.cfg file shows correct menuentries for Ubuntu and the necessary files seem to be there.  You might try disabling the separate EFI partition suggested by boot repair but I don't use UEFI myself so I'm not sure how you would do that.

---

### Post by childintime on 2015-11-28
> **yancek said:**
> What's on the 1TB drive?  The boot repair output shows windows code in the MBR.  You also show Grub code in the MBR of the first drive (750 GB) but you also have an EFI partition with the Ubuntu EFI files.  If you use EFI to boot, you should not have boot code in the MBR.  If you use MBR to boot, you don't need an EFI partition.  The grub.cfg file shows correct menuentries for Ubuntu and the necessary files seem to be there.  You might try disabling the separate EFI partition suggested by boot repair but I don't use UEFI myself so I'm not sure how you would do that.

1TB drive is just an external hard drive and does not play a role here. 

thx for taking a look

---

### Post by yancek on 2015-11-28
So what happens when you disable the EFI partition in boot repair?

---

### Post by childintime on 2015-11-28
> **yancek said:**
> So what happens when you disable the EFI partition in boot repair?

I get the message "grub is successfully repaired" but after reboot i still get into grub rescue command prompt.

---

### Post by oldfred on 2015-11-28
How you boot the Ubuntu installer, it then the default way Boot-Repair will repair your system. So if you boot in UEFI mode it will want to repair in UEFI boot mode. Or if booted in BIOS boot mode then it will repair in BIOS boot mode.
The difference is with UEFI you have grub-efi-amd64 for UEFI and grub-pc for BIOS. But install is otherwise the same, so you may have repaired grub in one mode but then in UEFI are booting in the other mode. Flash drive boot may not be same as hard drive boot, unless you have set that in UEFI.

I would review which way you are booting from UEFI boot menu. Is UEFI on, Secure boot off. Or is UEFI off and CSM/BIOS/Legacy boot mode on? It looks like you are currently configure for BIOS boto as the mount of the ESP - efi system partition is commented out in fstab.

You really do not have to turn off efi boot on drive, but control which way you boot from UEFI boot menu or perhaps one time boot key like f10 or f12.

What brand/model system?

---

### Post by childintime on 2015-11-29
Asus K56C laptop. Bios is called Asus Setup Utility Version 2.14.1226

I don't have UEFI menu as far as I understand, my Bios thing does not have a secure boot option. How do I set boot method then?

This is how my BIOS looks:

[http://i.imgur.com/ffru8Ck.jpg](http://i.imgur.com/ffru8Ck.jpg)
[http://i.imgur.com/uebPHHf.jpg](http://i.imgur.com/uebPHHf.jpg)
[http://i.imgur.com/wTK5D8P.jpg](http://i.imgur.com/wTK5D8P.jpg)
[http://i.imgur.com/agrHaeK.jpg](http://i.imgur.com/agrHaeK.jpg)

If I click add new boot option:
[http://i.imgur.com/FgDK97i.jpg](http://i.imgur.com/FgDK97i.jpg)

Also Save & Exit tab has "launch EFI shell from filesystem device" option, if that's relevant.

Also after I type the commands in grub rescue I get straight into normal Grub 2, so I think it is indeed installed.

---

### Post by oldfred on 2015-11-29
Have you updated UEFI from Asus to newest available for your system?
Not sure if Intel settings interfere or not.

Some perhaps similar models where users posted more details.
         [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[URL="http://ubuntuforums.org/showthread.php?t=2088499"]http://ubuntuforums.org/showthread.php?t=2088499
[/URL]
 Asus UltraBook - kernel comparisons K56CA
[URL="http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI"]http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI
      [/URL]
 Asus x55u UEFI change to BIOS discuses boot keys esp & f2, shows newer UEFI/BIOS screens:
[http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html](http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html)

    [URL="http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI"]
[/URL]

[URL="http://ubuntuforums.org/showthread.php?t=2088499"]
[/URL]

---

### Post by childintime on 2015-12-18
oldfred, I did not update. Thanks for your links.

Update:

1. Whenever I am booting into ubuntu I get "disk errors found" during boot.

2. So I did a regular restart after update today and now I cannot enter Ubuntu by entering the lines I've shown in the first post. Can't even see anything when doing "ls (hd0,gpt4)/boot".

So I got into Live USB, and run "sudo badblocks -sv /dev/sda" to check for bad sectors. Results: 5365 bad blocks found (5365/0/0 errors).

Also before installing new Ubuntu, and after installing I often have high I/O on hard disk.

Is this safe to assume that my hard disk is failing and I need to replace it?

---

### Post by TheFu on 2015-12-18
> **childintime said:**
> Is this safe to assume that my hard disk is failing and I need to replace it?

I would assume there is some issue with storage. Could be a cable, controller, or disk ... or it could just be a logical issue. 
I'd make certain my backups were 100% reliable and swap this disk with issues into a non-critical roll.  Until all the errors are gone (checking with badblocks and SMART data), I wouldn't re-use this disk for anything other than sneaker-net sharing with other people. Nothing critical.

However, sometimes a disk that reports problems is fine. After moving to a new system, new enclosure or new controller, if there aren't any SMART errors and badblocks reports zero issues, only then would I trust the drive again. The current contents of that disk shouldn't be trusted. They are likely corrupt even if you don't see any issues in file. The badblocks reporting is sufficient.

IMHO.

---

### Post by childintime on 2015-12-21
> **TheFu said:**
> I would assume there is some issue with storage. Could be a cable, controller, or disk ... or it could just be a logical issue. 
I'd make certain my backups were 100% reliable and swap this disk with issues into a non-critical roll.  Until all the errors are gone (checking with badblocks and SMART data), I wouldn't re-use this disk for anything other than sneaker-net sharing with other people. Nothing critical.

However, sometimes a disk that reports problems is fine. After moving to a new system, new enclosure or new controller, if there aren't any SMART errors and badblocks reports zero issues, only then would I trust the drive again. The current contents of that disk shouldn't be trusted. They are likely corrupt even if you don't see any issues in file. The badblocks reporting is sufficient.

IMHO.

Understood. But if I still have warranty for my laptop, do I just bring laptop to them and explain everything? Will they be able to see that HDD is indeed faulty? Because OS is working, just a lot of bad sectors as you can see.

---

### Post by TheFu on 2015-12-24
Don't know anything about the warranty on your laptop. You'd have to ask them.  Plus, were I live, it is unlikely they'd touch a system with Linux installed, so I'd need to get Windows back on the device ... and they'd probably just replace the old disk with a newer-to-me disk and a factory reset. That tends to be the answer for everything - factory reset.  Anytime I give a HDD to someone else, I assume all the contents will be copied and I'll never see it again.  With a system, the HDD will be factory reset will all data wiped.

But your warranty might be something different. I dunno.

---

### Post by childintime on 2015-12-30
> **TheFu said:**
> Don't know anything about the warranty on your laptop. You'd have to ask them.  Plus, were I live, it is unlikely they'd touch a system with Linux installed, so I'd need to get Windows back on the device ... and they'd probably just replace the old disk with a newer-to-me disk and a factory reset. That tends to be the answer for everything - factory reset.  Anytime I give a HDD to someone else, I assume all the contents will be copied and I'll never see it again.  With a system, the HDD will be factory reset will all data wiped.

But your warranty might be something different. I dunno.

I got new SSD and put Xubuntu on it, and everything works brilliantly! Most likely old HDD was broken because I had so many issues.

Thank you everyone

---

