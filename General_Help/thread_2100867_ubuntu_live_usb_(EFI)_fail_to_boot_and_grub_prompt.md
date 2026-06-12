---
title: "ubuntu live usb (EFI) fail to boot and grub prompt appears"
date: 2013-01-03
forum: General Help
---

### Post by yurovisk on 2013-01-03
Hi all!

I bought an Ultrabook Dell Inspiron 14z 5423 with Windows 8 and want to install Ubuntu with dual boot.

The problem is that when I try to boot the live usb of ubuntu (or Debian testing or Ubuntu-secure-remix) in EFI mode grub prompt appears instead of grub menu (non-EFI boot works fine). 

I tried with and without Secure Boot (I know that debian doesnt support Secure Boot yet) and tried Unetbootin, lili usb creator and universal usb installer with same results.

I looked for something like quick boot or fast boot to deactivate too and found "Intel's Rapid Start Technology" and deactivated too.

My BIOS firmware is up to date and I dont know what to do.

Thanks for the support! :)

---

### Post by oldfred on 2013-01-03
UltraBooks have the Intel SRT which complicates it. You have to turn that off. Some have just used SSD for Ubuntu others install to hard drive then turn Intel back on.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> 
Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.

   
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

    

---

### Post by Kevin McCready on 2013-01-11
This is all new to me and I have my own grub problems which I've posted to the forum (no answer yet). But I'm working my way through [Grub from the Ground Up]("http://www.troubleshooters.com/linux/grub/grub.htm").

Good luck

---

### Post by oldfred on 2013-01-11
@Kevin McCready
Your link is old and is to grub legacy, so it does not apply at all to grub2 either BIOS/MBR or UEFI/gpt.
Start your own thread and post BootInfo from Boot-Report.

---

### Post by yurovisk on 2013-01-24
So...
I deactivated Intel SRT and changed SATA mode to AHCI.

Oldfred I don't know if you really noticed (just to make sure) but my initial problem was that I can't boot the LIVE USB ubuntu (nor debian, nor ubuntu secure remix) in EFI mode. I didn't install any OS at this time. 

Unfortunately deactivate Intel SRT and change the SATA mode  didn't change that.

So I created partitions freeing space of the Windows 8 partitions  and installed Debian 64 bit Wheeze (testing) in NON-EFI mode (skiping the grub install) and used the Boot Repair of the Ubuntu-Secure-Remix LIVE USB in NON-EFI mode to turn the system to EFI.
Boot Repair reports that my grub is OK. And here is the log: [http://paste.ubuntu.com/1565133/](http://paste.ubuntu.com/1565133/)
And now I can boot Windows from Grub, but not Debian.  :(

When I try to boot Debian the unique thing that I see is a black screen.

Interesting fact:
-Initially I tried to boot debian/ubuntu live usb in EFI that was maked  with tools in Windows 8 (unetbootin and others). And the result was(as previously reported) a grub console when I try to boot. But when I used the "Make startup disk" of an ubuntu PC to make the ubuntu-secure-remix live usb the result was like when I try to boot the installed Debian (a black screen).

My guess is that is occurring the same with my installed Debian "fixed" by the Boot Repair and with the Live Usb of the Ubuntu Secure Remix.

---

### Post by oldfred on 2013-01-24
I know several have installed Ubuntu in BIOS/legacy mode and Boot-Repair will convert to UEFI mode.  A few had to do it that way as they also had issues booting liveCD in UEFI mode, most did it accidentally.

Do not know about Debian but I did not know it had UEFI mode enabled. Ubuntu is one of the few with secure boot.

        The State Of Linux Distributions Handling Secure Boot
[http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI](http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI)

It looks like you still have the Intel SRT enabled as it is showing RAID type partition mounts. 

Some of the issues are just that vendors have not made systems with UEFI that easily dual boot.

It also looks like the SSD is 32GB but Intel SRT only uses 8GB for Windows cache?

---

### Post by yurovisk on 2013-01-24
I know it is possible to boot debian in efi because exists this tutorial(that did not worked with me): [http://tanguy.ortolo.eu/blog/article51/debian-efi](http://tanguy.ortolo.eu/blog/article51/debian-efi)
And Boot Repair works with debian too (informations on the boot repair website).

Debian doesn't have support to secure boot yet.

And Secure Boot is disabled in my Bios (I dont know why but looks like windows still works so).

Intel SRT is disabled in my BIOS and when I boot windows the intel application messages me that "Looks like you are not using intel SRT". 
I omitted in the last post that before the Debian installation I executed a "sudo dmraid -E -r /dev/sda".
But I think that I didn't make a "sudo dmraid -E -r /dev/sdb".

Intel SRT divides the SSD in 8GB and 22GB.
See post #5 in the first image of the tutorial: [http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
 I don't know why gparted recognizes just one partition. The format of the partitions may not be the same.

---

### Post by oldfred on 2013-01-25
If you can get to grub menu you are efi booting.
Then it may be boot parameters or other kernel or driver issues.

This is for Ubuntu:
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

