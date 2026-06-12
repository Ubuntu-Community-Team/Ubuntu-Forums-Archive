---
title: "Can't boot back into Windows after Ubuntu dual installation. Bootrepair doesn't help"
date: 2015-08-19
forum: General Help
---

### Post by benjamin46 on 2015-08-19
So, the other day I installed Ubuntu on my home built PC. Previously I was just running Windows 10 (updated a week ago). As I was installing Ubuntu 14.04 for a few uni projects, on installation I created a partition of just 60GB for the Ubuntu. I should note that I have two drives - Windows is on my 128SSD, Ubuntu is on a 60GB partition on my 1TB HD.

So Ubuntu has worked fine but now that I've wanted to boot back into windows I can't find away. I have both Grub and BootRepair installed on Ubuntu. I'm not an expert at linux by any means, but I'm pretty sure I have Grub installed so that it should open when I boot the PC - instead however, after 10seconds of no screen output, it boots straight into Ubuntu. I also tried BootRepair. I ran the recommended fix, and this did nothing. I also went into the advanced settings and changed to boot into Windows, however the PC still booted into Ubuntu and when I went back to BootRepair, the OS default I had set had reverted back to being Ubuntu.

Another thing, I tried ripping out the Ubuntu HDD and booting the PC, but the PC would turn on and there would be no screen output. I only did this once though.

Sorry if this seems really amateur - I just really need to log back onto Windows for other uni work.

---

### Post by benjamin46 on 2015-08-19
I also got this from bootrepair:
[http://paste.ubuntu.com/12124585](http://paste.ubuntu.com/12124585)

---

### Post by kansasnoob on 2015-08-19
In BIOS do you have the boot priority set to boot the 1 TB drive first:

> Please do not forget to make your BIOS boot on sdb (1000GB) disk!


Should be a place where you can set hard drive boot priority - sometimes named oddly just to confuse.

---

### Post by benjamin46 on 2015-08-20
Here's another silly question... How do I do that from within Ubuntu? I've tried searching around but can't find anything that I understand.

---

### Post by yancek on 2015-08-20
You can't do it from within Ubuntu or any other operating system.  When you boot the computer, the first thing you should see is the logo of the manufacturer on screen and at the bottom there should be a message telling you which key to hit to enter BIOS, sometimes called setup.  Hit that and look for boot options.

---

### Post by benjamin46 on 2015-08-20
That doesn't happen and I can't figure out how to make it happen. When I boot, there's 10 seconds of no screen output and then eventually the Ubuntu logo comes on. I've tried hitting the F2 key after booting but for some reason this actually just stops anything from happening and the screen doesn't come on... it's really bizarre. I know what to do when I can get into the BIOS, the thing is I just have no clue about getting there now that it won't come up.

---

### Post by benjamin46 on 2015-08-21
The PC won't even boot from the disk I used to install Ubuntu... it just gets stuck on the ubuntu loading screen.

---

### Post by yancek on 2015-08-21
Have you entered the BIOS previously by using the F2 key?  Are you sure that is correct?  If you are not seeing the manufacturer logo but just going straight to Ubuntu, something else is wrong.

Look at the top of the boot repair output.  It shows Grub code in the master boot record of the first drive (sda) which is your windows drive and it points to the Ubuntu install on the second drive.  You have syslinux code installed in the mbr of the second (1TB) drive.  Your Grub boot files are on sdb5 and the grub.cfg file shows two windows entries.  Do you not see these on the menu or do you not see a menu at all.

I see you also have Grub files on sdb2 which is an ntfs partition.  Not good but I doubt this is the cause of the problem.  Also, the grub.cfg file (Grub Menu) shows correct entries for windows.  If you are unable to access the BIOS, there really isn't anything you can do with Ubuntu to change that.  How old/new is this computer?

---

### Post by oldfred on 2015-08-21
The key you press to get into BIOS varies by vendor, often del or f2.

 BIOS Setup Utility Access Keys for Popular Computer Systems
[http://pcsupport.about.com/od/fixtheproblem/a/biosaccess_pc.htm](http://pcsupport.about.com/od/fixtheproblem/a/biosaccess_pc.htm)
UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

From Boot-Repair's advanced mode you should choose Ubuntu and install grub to sdb. And choose Windows and install a Windows boot loader to sda. Then in BIOS set drive that is sdb as first in BIOS boot order. Or use one time boot key, often f10 or f12, see links above for your brand on most likely key.

---

### Post by benjamin46 on 2015-08-22
> **yancek said:**
> Have you entered the BIOS previously by using the  F2 key?  Are you sure that is correct?  If you are not seeing the  manufacturer logo but just going straight to Ubuntu, something else is  wrong.

Do you not see these on the menu or do you not see a menu at all?

I don't see a menu at all. After powering on, the computer takes about 15 seconds before it outputs anything to my monitor. Then the first thing I see is the Ubuntu loading screen. I don't see the GIGABYTE logo.

I had it mixed up - it's actually the DEL key, but even so, if I press any key after I've booted the system my computer does nothing. I get no output to my monitor and it just sits there doing nothing indefinitely.

Should I try uninstalling grub from the NFTS partition? Is there a specific way to do this - sorry, I'm really unfamilliar with linux.

> **yancek said:**
>  How old/new is this computer?  

It's only just over a year old, and I'm really doubting that it's something hardware related. I've never had trouble getting into the BIOS before and the system ran like a dream right up until I installed Ubuntu about a week ago.

---

### Post by benjamin46 on 2015-08-22
> **oldfred said:**
> The key you press to get into BIOS varies by vendor, often del or f2.

From Boot-Repair's advanced mode you should choose Ubuntu and install grub to sdb. And choose Windows and install a Windows boot loader to sda. Then in BIOS set drive that is sdb as first in BIOS boot order. Or use one time boot key, often f10 or f12, see links above for your brand on most likely key.

Thanks for pointing me to those links. I worked out that I had the wrong key - it's actually the DEL key... It still doesn't work for me though :( Any attempt to get into the BIOS and my computer just doesn't boot - it doesn't output to the monitor or anything.

I tried those points you said but still nothing. Is there anything else you can suggest?

All I need right now is to just get back into Windows - even if it means removing Ubuntu completely (I can still use it on the computers at uni).

---

### Post by oldfred on 2015-08-22
Which Gigabyte board?

       Gigabytes P67 & H67 hybrid efi -Hybrid EFI is a UEFI based on the open source TianoCore
[http://www](http://www).[rod]("http://www.rodsbooks.com/gb-hybrid-efi/")sbooks.com/gb-hybrid-efi/
[http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html](http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html)
Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

Some need a full cold boot or power down, (if laptop remove battery), hold power switch for 10 sec or so to drain left over power and then reboot immediately pressing correct key.
A few have to jumper pins or move jumper for 10 sec with power off on motherboard. See manual. That will most likely reset all UEFI/BIOS settings to defaults.  Same with UEFI updates in returning to defaults. Did you install newest update to UEFI/BIOS from gigabyte? 
When I updated BIOS on my old system I had to take photos of screens to remember all the changes I make. My new Asus UEFI system lets me take screenshots & save to system, If file system is writeable somewhere.

---

### Post by benjamin46 on 2015-08-23
> **oldfred said:**
> Which Gigabyte board?



It's a 787X-HD3. I tried clearing the CMOS as per manufacturers instructions but now the computer won't even boot into Ubuntu - there's just no screen output at all now. My only option left is to replace the motherboard - lucky it's in warranty.

Thanks so much for your help and those links! I had no idea that about clearing the CMOS - so I've learnt something valuable. Hopefully this is just the Motherboard and everything will be sweet with a new one.

---

### Post by oldfred on 2015-08-23
Motherboard may be ok, just when you reset system, it reverted to all the defaults in UEFI.
And you have to then reset Ubuntu as first in boot order if UEFI or if in CSM/BIOS/Legacy mode turn off UEFI and turn on CSM mode.
And links above mention other settings that you may have to change.
Your motherboard may have a fast boot setting and that is why you cannot get into UEFI. The fast boot in UEFI skips all hardware checking and just boots as if nothing has changed. Since that is often the case it does offer faster boot. But when you want to get into UEFI you cannot without major issues.

My Asus had several fast boot settings. One for cold boot which I left at normal and for warm/reboot I set it to 3 sec delay so I have a chance to press key to get into UEFI.

---

