---
title: "Can't install Ubuntu 16.04 from bootable USB (dual boot)"
date: 2017-08-06
forum: General Help
---

### Post by egomidor on 2017-08-06
[COLOR=#111111][FONT=Ubuntu]I've been trying to install Ubuntu 16.04 alongside Windows 10 64 bit. I've burnt the iso image into a USB stick (with Rufus) and disabled fast boot and secure boot and changed the boot order but when I restart the computer it still boots to Win10. I've also updated the BIOS to it's latest version.

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I'm using an Acer Aspire E1-572PG.

If I boot in Legacy mode then it boots the USB but it says "This[/FONT][/COLOR] computer currently has no detected operating systems".

What should I do now to boot the USB in UEFI mode and properly understand Ubuntu?

---

### Post by oldfred on 2017-08-06
Some Acer need additional boot parameters.
All Acer once installed need you to have updated UEFI, and with Secure boot on, set UEFI password and then from inside UEFI set "trust" on the ubuntu/grub .efi boot files.

Other similar Acer:
 Acer Aspire ES (15 ES1-523-844Y)  works with some settings
[https://ubuntuforums.org/showthread.php?t=2364018](https://ubuntuforums.org/showthread.php?t=2364018)
Acer Aspire ES1-132 cannot able to install kubuntu UEFI missing options, rEFInd
[https://ubuntuforums.org/showthread.php?t=2348269](https://ubuntuforums.org/showthread.php?t=2348269) 
      
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer ES1-331 laptops Strange differences at new installations
[URL="https://ubuntuforums.org/showthread.php?t=2362511"]https://ubuntuforums.org/showthread.php?t=2362511
[/URL]
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)
One of several with more details on trust:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335) 

[URL="https://ubuntuforums.org/showthread.php?t=2362511"]
[/URL]

---

### Post by egomidor on 2017-08-06
The problem is that I can't even install Ubuntu so I can't even set the efi files to trusted in the UEFI settings. The USB doesn't book unless I boot it in Legacy mode.

---

### Post by oldfred on 2017-08-06
Did you verify download?
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Do you have a setting in UEFI to allow USB boot?]
If Secure Boot is on, that often is another setting, but you may need to set a UEFI password to see that setting.

Some systems work with one USB port but not another.
Some installers work where others do not.
And some flash drives work where others do not. 
So you just have to experiment a bit.

---

### Post by egomidor on 2017-08-07
These are the options available in my BIOS. I've tried all the three USB ports but with these settings it doesn't working. Yes, I verified the downloaded iso file.
[ATTACH=CONFIG]276282[/ATTACH][ATTACH=CONFIG]276283[/ATTACH][ATTACH=CONFIG]276284[/ATTACH]

---

### Post by oldfred on 2017-08-07
While it should boot in UEFI mode, try with Secure boot off.

---

### Post by egomidor on 2017-08-07
I've tried that too. I really don't know what I'm doing wrong. :(

---

### Post by oldfred on 2017-08-07
Have you updated UEFI?
Some versions were not good from Acer.
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 
      
 Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)

---

### Post by egomidor on 2017-08-07
Yes, I updated UEFI to it's latest version from the offical Acer website.

---

### Post by oldfred on 2017-08-07
It seems like you have done everything correctly?
If you create a UEFI only flash drive, will your system see it?
       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

Some more comments by Acer users with issues.
[https://askubuntu.com/questions/921857/bootable-device-not-found-ubuntu-16-04-no-option-in-bios-to-select-an-uefi-fil](https://askubuntu.com/questions/921857/bootable-device-not-found-ubuntu-16-04-no-option-in-bios-to-select-an-uefi-fil)

---

### Post by egomidor on 2017-08-08
Well it seems like I shouldn't have burnt the iso with Rufus. I've just copied everything to the USB stick like you told me and now it works fine. Thank you very much for your help. :)

---

### Post by oldfred on 2017-08-08
Please change to Solved so others can find solution.
But I thought Rufus worked, at least for some? Never used it myself.

---

