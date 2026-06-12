---
title: "How do I dual boot windows 8.1 and ubuntu 15.04"
date: 2015-07-18
forum: General Help
---

### Post by theking36 on 2015-07-18
So I'm trying to dual boot both windows 8.1 an ubnutu 15.04. I keep seeing people telling me to do different things and I don't know which one is right. Anyone can tell me what to do correctly? My computer is not a laptop or pre-built I made it by myself if that helps

---

### Post by oldfred on 2015-07-19
Is this a new computer with UEFI and CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Post details, motherboard, cpu, RAM, video chip/card and number of drives.

BIOS with MBR partitioning has been around since the very first PC in the early 1980's. So well known, but many fixes to make it work with newer hardware over the years.

UEFI is relatively new. But all new Apple Macs with Intel chips use an early version of UEFI. And all pre-installed Windows 8 systems use UEFI. But you can install Windows 8 in either mode. And Windows requires partitioning of drive to match install or UEFI must be gpt, and BIOS must the the old MBR(msdos).

You do have to be sure to install both systems in same boot mode, or both UEFI or both BIOS. And for both Windows & Ubuntu how you boot install media is then how it installs, it is not an option once you booted. UEFI & BIOS are not compatible and once you start booting in one mode you cannot change to the other. 

So instructions will vary based on hardware. 
And then if UEFI capable if you want UEFI or BIOS.

My new desktop is an Asus-ar motherboard with Intel i5. I have a nVidia card and two drives, SSD for booting and 1TB hard drive for data. No Windows but up to 3 installs so far of Ubuntu.
System is UEFI, but I had to make a lot of setting changes in UEFI to get to correctly boot in UEFI mode.

---

### Post by theking36 on 2015-07-19
I think my computer is in bios mode not uefi because running msinfo32 shows legacy
> **oldfred said:**
> Is this a new computer with UEFI and CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Post details, motherboard, cpu, RAM, video chip/card and number of drives.

BIOS with MBR partitioning has been around since the very first PC in the early 1980's. So well known, but many fixes to make it work with newer hardware over the years.

UEFI is relatively new. But all new Apple Macs with Intel chips use an early version of UEFI. And all pre-installed Windows 8 systems use UEFI. But you can install Windows 8 in either mode. And Windows requires partitioning of drive to match install or UEFI must be gpt, and BIOS must the the old MBR(msdos).

You do have to be sure to install both systems in same boot mode, or both UEFI or both BIOS. And for both Windows & Ubuntu how you boot install media is then how it installs, it is not an option once you booted. UEFI & BIOS are not compatible and once you start booting in one mode you cannot change to the other. 

So instructions will vary based on hardware. 
And then if UEFI capable if you want UEFI or BIOS.

My new desktop is an Asus-ar motherboard with Intel i5. I have a nVidia card and two drives, SSD for booting and 1TB hard drive for data. No Windows but up to 3 installs so far of Ubuntu.
System is UEFI, but I had to make a lot of setting changes in UEFI to get to correctly boot in UEFI mode.

---

### Post by oldfred on 2015-07-19
From Ubuntu live installer's terminal, post this:
sudo parted -l

In your UEFI boot tab, should have been two boot modes for Windows flash drive and with Ubuntu you will get two boot modes.
Usually it shows UEFI:name and name where name is the name or label of the flash drive. The UEFI entry boots in UEFI mode and the plain name boots in BIOS mode.

If you have Windows 8 installed whether BIOS or UEFI, you must turn off fast startup or its always on hibernation.
       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

And you should turn off fast boot setting in UEFI. Mine had two settings, one cold boot and one warm reboot. And I could set time delay. So I set cold boot to fast boot off, and warm boot to 3 sec delay. Some that leave fast boot on then cannot get into UEFI to change settings. System may be configured to only get into UEFI from Windows entry. But if Windows breaks, you cannot get into UEFI to even choose to boot a USB repair flash drive.

---

### Post by theking36 on 2015-07-19
> **oldfred said:**
> From Ubuntu live installer's terminal, post this:
sudo parted -l

In your UEFI boot tab, should have been two boot modes for Windows flash drive and with Ubuntu you will get two boot modes.
Usually it shows UEFI:name and name where name is the name or label of the flash drive. The UEFI entry boots in UEFI mode and the plain name boots in BIOS mode.

If you have Windows 8 installed whether BIOS or UEFI, you must turn off fast startup or its always on hibernation.
       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

And you should turn off fast boot setting in UEFI. Mine had two settings, one cold boot and one warm reboot. And I could set time delay. So I set cold boot to fast boot off, and warm boot to 3 sec delay. Some that leave fast boot on then cannot get into UEFI to change settings. System may be configured to only get into UEFI from Windows entry. But if Windows breaks, you cannot get into UEFI to even choose to boot a USB repair flash drive.
I don't get this. So while installing ubuntu you want me to run sudo parted -I. What do you mean by uefi boot tab? I haven't installed ubuntu yet?

---

### Post by oldfred on 2015-07-19
To boot Ubuntu you have to go into UEFI and select to boot flash drive.

And the installer is a live system as well. Always best to boot in live mode and test that things work.

Knowing your partitions, helps confirm if UEFI or BIOS boot install.

You have not posted hardware?

Attached shows one users UEFI with two options to boot Toshiba flash drive, one UEFI and one not. But every UEFI has different screens, so your may vary.

---

### Post by theking36 on 2015-07-19
> **oldfred said:**
> To boot Ubuntu you have to go into UEFI and select to boot flash drive.

And the installer is a live system as well. Always best to boot in live mode and test that things work.

Knowing your partitions, helps confirm if UEFI or BIOS boot install.

You have not posted hardware?

Attached shows one users UEFI with two options to boot Toshiba flash drive, one UEFI and one not. But every UEFI has different screens, so your may vary.
Oh now I know what u meant by uefi. My hardware is an i3 4170, gigabyte b85m ds3h mobo, r9 280x if that helps. U want me to post partitions? I have not yet shrink my partitions yet. So when I go into uefi boot tab do I boot into the one that doesn't say uefi? Since my bios mode is legacy.

---

### Post by oldfred on 2015-07-19
Do not know about AMD. That may need a boot parameter to have video work correctly.
Is your UEFI/BIOS the most current version from Gigabyte?
Have you used all 4 primary partitions? Still best to post partitions, so we know.

All Gigabyte boards seem to have issues with IOMMU. USB ports may not work.
Not sure if just an issue with UEFI and not BIOS? 
Most with new hardware want to take advantage of newer UEFI. But some want the old BIOS as they know it better.

 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

Use Windows to shrink Windows NTFS partition and reboot into Windows immediately so it can run chkdsk which it needs after any resize. And make sure fast startup is off which is always on hibernation. Linux will not correctly see Windows as it does not mount a NTFS partition that needs chkdsk or is hibernated to prevent damage. But without seeing it, it may cause other issues.

Make sure you have good backups. If you have original Windows installer know how to get into its repair console just in case. Or make a Windows repair CD/flash drive.

Post partitions just to know, but if you are sure you are CSM/BIOS then you have to boot entry without UEFI.
While more for UEFI boot, it also shows the BIOS screen, just so you know which way you are booting.
Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
      
 Also shows Windows 8 screens, Only real difference in UEFI and BIOS install is how you initially boot. And whether drive is gpt or MBR.
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

---

### Post by theking36 on 2015-07-19
> **oldfred said:**
> Do not know about AMD. That may need a boot parameter to have video work correctly.
Is your UEFI/BIOS the most current version from Gigabyte?
Have you used all 4 primary partitions? Still best to post partitions, so we know.

All Gigabyte boards seem to have issues with IOMMU. USB ports may not work.
Not sure if just an issue with UEFI and not BIOS? 
Most with new hardware want to take advantage of newer UEFI. But some want the old BIOS as they know it better.

 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

Use Windows to shrink Windows NTFS partition and reboot into Windows immediately so it can run chkdsk which it needs after any resize. And make sure fast startup is off which is always on hibernation. Linux will not correctly see Windows as it does not mount a NTFS partition that needs chkdsk or is hibernated to prevent damage. But without seeing it, it may cause other issues.

Make sure you have good backups. If you have original Windows installer know how to get into its repair console just in case. Or make a Windows repair CD/flash drive.

Post partitions just to know, but if you are sure you are CSM/BIOS then you have to boot entry without UEFI.
While more for UEFI boot, it also shows the BIOS screen, just so you know which way you are booting.
Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
      
 Also shows Windows 8 screens, Only real difference in UEFI and BIOS install is how you initially boot. And whether drive is gpt or MBR.
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
OK so I will post partitions after I eat.  What about the bootloader everything will work fine right.
So the instructions are
1 disable fast boot
2 shrink windows partition 
3 boot from usb drive (not the uefi one)
4 run command u told me before
5 go through install process
6 click where it says at top to install ubuntu with windows 8.1 side by side
7 wait
8 success (hopefully) 
If these are the instructions tell me and I will do them

---

### Post by theking36 on 2015-07-19
Here is partitions [http://i.imgur.com/p8yNG5J.jpg](http://i.imgur.com/p8yNG5J.jpg)

---

### Post by oldfred on 2015-07-19
Reboot Windows before booting into live installer after resize. It needs to run chkdsk.

Best to test in live mode before installing. Helps learn a bit about Ubuntu and verify that it works with your system.

Did you make the settings changes in UEFI/BIOS for IOMMU?

---

### Post by theking36 on 2015-07-20
> **oldfred said:**
> Reboot Windows before booting into live installer after resize. It needs to run chkdsk.

Best to test in live mode before installing. Helps learn a bit about Ubuntu and verify that it works with your system.

Did you make the settings changes in UEFI/BIOS for IOMMU?

No I did not make changes

---

### Post by gabriel50 on 2015-07-20
Look, to dual boot, you only need uefi in the Bios Conf like Olfred told you. Most of the computers brings this option by default. You made the partition so now, just install ubuntu, restart and you'll get the Grub with the option to select the SO you want. It should show up the grub automatically.

---

### Post by theking36 on 2015-07-20
> **gabriel50 said:**
> Look, to dual boot, you only need uefi in the Bios Conf like Olfred told you. Most of the computers brings this option by default. You made the partition so now, just install ubuntu, restart and you'll get the Grub with the option to select the SO you want. It should show up the grub automatically.

Sorry what do you mean by uefi in bios configuration? I'm still a noob to this. Like enabling uefi or something?

---

### Post by gabriel50 on 2015-07-20
sorry i made a mistake.... it wasn't: in, i meant: or...
it doesn't matter..

this is a simple mode, get into the bios with F2 or F12 or the indicated key, and search for Legacy boot, and enable it.... then install linux in the partition you made.... Don't worry, unless you delete the windows partition won't be any problem it can't be solved.... But you shouldn't have any kind of trouble... If you want to be sure, make a backup first so you can work unconcerned

Edit: what  i mean about deleting windows partition and the backup is, just if you commit a mistake when installing linux or making the partition. Enabling Boot legacy won't do that in any way.... Boot legacy just give you the possibility to have a dual boot. this Is the way i've always done it...

---

### Post by oldfred on 2015-07-20
If Windows is booted in UEFI boot mode, you do not want Ubuntu in BIOS/Legacy mode.
But if Windows is in BIOS mode you do want Ubuntu installed in BIOS/legacy mode.
Both systems must be in same boot mode to avoid issues.

It is possible to boot when in different modes if Windows is UEFI and Ubuntu legacy, but only by going into UEFI and turning on UEFI for Windows and turning off UEFI and turning on Legacy for BIOS boot. Some will auto switch and let you use one time boot key like f12. 

But if not in same boot mode, then you cannot use grub to dual boot, only UEFI boot menu.

---

### Post by theking36 on 2015-07-28
> **oldfred said:**
> If Windows is booted in UEFI boot mode, you do not want Ubuntu in BIOS/Legacy mode.
But if Windows is in BIOS mode you do want Ubuntu installed in BIOS/legacy mode.
Both systems must be in same boot mode to avoid issues.

It is possible to boot when in different modes if Windows is UEFI and Ubuntu legacy, but only by going into UEFI and turning on UEFI for Windows and turning off UEFI and turning on Legacy for BIOS boot. Some will auto switch and let you use one time boot key like f12. 

But if not in same boot mode, then you cannot use grub to dual boot, only UEFI boot menu.
Ok so now I'm trying to boot into Ubuntu through the usb but it only shows up the one with uefi at the start, not the one without it

---

### Post by oldfred on 2015-07-28
You need to make sure in UEFI/BIOS that you have secure boot off, UEFI off, and legacy/BIOS/CSM mode on. 

So you know which way you have booted, this shows initial screens for BIOS & UEFI(grub menu)
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

      
 [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)

---

### Post by theking36 on 2015-07-28
> **oldfred said:**
> You need to make sure in UEFI/BIOS that you have secure boot off, UEFI off, and legacy/BIOS/CSM mode on. 

So you know which way you have booted, this shows initial screens for BIOS & UEFI(grub menu)
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

      
 [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
still doesn't work. I had secure boot disabled 
[http://i.imgur.com/ZGaEt7d.jpg](http://i.imgur.com/ZGaEt7d.jpg)

---

### Post by MGrowl on 2015-07-28
Make sure that whatever device you have the ubuntu iso on  boots first in the bios's boot order. This should be pretty straightforward along with the installation. Try to read up more. EVERYTHING is covered in detail and the basics of installation and usage are all over the net. Unless you enjoy tinkering around with your system, because eventually you'll run into some problems in linux, like we all do, that need a little tweaking underneath the hood. If you're comfortable with that dive right in I'm sure you'll enjoy linux. Otherwise, it be best to stick to windows.

Windows 8.1/Ubuntu dual boot: [URL="http://ubuntuforums.org/showthread.php?t=2187907"]
http://ubuntuforums.org/showthread.php?t=2187907[/URL]
[http://www.instructables.com/id/Dual-Boot-Ubuntu-and-Windows-8-UEFI/](http://www.instructables.com/id/Dual-Boot-Ubuntu-and-Windows-8-UEFI/)
[http://ubuntuforums.org/showthread.php?t=2188402](http://ubuntuforums.org/showthread.php?t=2188402)

---

### Post by oldfred on 2015-07-28
Did you change UEFI to CSM only, not even UEFI & CSM?
And change USB boot to CSM only?

How did you make flash drive? 
If you just extract ISO to flash drive it is UEFI only. If you use one of the tools like unetbootin to extract, it also creates the BIOS boot configuration on flash drive.

---

### Post by theking36 on 2015-07-28
> **oldfred said:**
> Did you change UEFI to CSM only, not even UEFI & CSM?
And change USB boot to CSM only?

How did you make flash drive? 
If you just extract ISO to flash drive it is UEFI only. If you use one of the tools like unetbootin to extract, it also creates the BIOS boot configuration on flash drive.
I used rufus then tried universal usb installer 
I'll go check if uefi is set to csm  only

---

### Post by theking36 on 2015-07-28
> **theking36 said:**
> I used rufus then tried universal usb installer 
I'll go check if uefi is set to csm  only

Digging through bios settings i was able to boot into bios mode and installed ubuntu. thanks for all the help!

---

### Post by oldfred on 2015-07-28
Glad you found correct settings and got it installed. :)

On my Asus motherboard, it was just the opposite. It would only boot in CSM mode. I had to change many setttings and tell it UEFI only on external devices to finally get to boot in UEFI mode.

---

