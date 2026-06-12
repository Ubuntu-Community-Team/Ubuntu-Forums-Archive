---
title: "Deleted Partition Causing Boot Error"
date: 2017-08-07
forum: General Help
---

### Post by supersayan22 on 2017-08-07
I have an Acer Aspire E3-111 running Windows 10. It was very slow, so I decided to jump ship to Lubuntu. It was running fine until I noticed that it would not boot to the Acer Logo. I decided to delete the whole entire hard drive and start over. I accidently deleted a small partition around 500 MB titled UEFI. When I restarted the computer, I get a blank screen and then a blue message saying "Default Boot Device or Boot Failed. Insert Recovery Media and Hit any Key. Then Select 'Boot Manager' to choose a new Boot Device or to Boot Recovery Media." When I am taken to the boot menu, I see options for Ubuntu, HDD, and Windows Manger. Clicking any of them brings back to the blue dialog. Inserting a SD card and USB drive does not show up in the options. I am not really sure what to do. My absolute back up plan is to take out the hard drive and install Lubuntu through another machine and see if it fixes the issue. I would appreciate any advice. I am a novice user trying to understand computers.

---

### Post by VMC on 2017-08-07
When Acer logo appears, does Alt+F10 show recovery options?

---

### Post by supersayan22 on 2017-08-08
[FONT=arial]No. I am not even getting an Acer logo. It goes straight to the blue dialog error. [/FONT]

---

### Post by oldfred on 2017-08-08
That sounds more like a Windows or perhap UEFI boot error.

If you have a correctly configured UEFI boot key you should be able to choose that from UEFI boot menu to boot into Ubuntu live installer. Then you can make repairs.

Some UEFI systems have fast boot on. You may have to cold boot or full power down including removing battery and holding power switch for 10 sec to fully drain system. Some have to remove motherboard battery or jumper pins on motherboard to get a full UEFI reset. But then you should be able to get into UEFI and select USB flash drive.

One Acer user just could not boot a rufus created flash drive but a UEFI only USB drive worked.
[https://ubuntuforums.org/showthread.php?t=2368050](https://ubuntuforums.org/showthread.php?t=2368050)
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 

If you install from another system, it may not boot without adding an UEFI entry.
And Acer all require a supervisory password and setting of trust on .efi boot files.
      
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 
            Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

---

### Post by supersayan22 on 2017-08-09
[FONT=arial]Thanks for the information. I am beginning to understand what is happening. I will reply back when I try some of these suggestions.[/FONT]

---

### Post by supersayan22 on 2017-08-21
I tried most of these steps and none of them seem to be working. I went ahead and formatted the entire hard drive on another computer. I am still getting the same blue error message with missing boot drive. I am open for suggestions.

---

### Post by oldfred on 2017-08-21
Now this should be a new thread as a totally different system.

What brand/model system?
What video card/chip?

Install in UEFI or BIOS boot mode?

Is UEFI secure boot off if UEFI?
Is UEFI fast boot off if UEFI?
Did you install boot loader to sda, not anyplace else?

Have you reviewed link in my signature?

---

### Post by supersayan22 on 2017-08-22
I have  not checked the last link in your signature. I will see what I can gather. It is UEFI last I checked with fast boot. I did not install boot loader to sda ( I am assuming that it is native hard drive). The computer is an Acer Aspire E3-111 with 2GB of RAM and Intel Celeron with onboard graphics.

---

### Post by oldfred on 2017-08-22
If an Acer with UEFI, you need the 'trust' settings.

---

### Post by supersayan22 on 2017-08-23
I read that before. I understand what it means, but I am unable to even access the bios. It even refuses to boot from an removable media.

---

### Post by oldfred on 2017-08-23
If you left fast boot on in UEFI, then you may have trouble getting back into UEFI. Assumption is you always get into UEFI from Windows.
And fast boot assumes no system changes, or what UEFI has written onto drive for operating system is identical & UEFI immediately jumps to booting assuming it works. It is so fast you do not normally have time to press a key from UEFI until system starts (or fails) to boot.

Usually a full "cold" boot will then have UEFI recheck system and give you time to press keys to get back into UEFI. You need to totally power off, if laptop remove battery and hold power switch to drain any power left in system. Then boot.
If that does not work you often have to remove motherboard coin battery or jumper pins next to that battery to reset system. If you made any UEFI system setting changes you have to totally redo them.

---

