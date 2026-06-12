---
title: "Running Ubuntu from external drive."
date: 2013-01-17
forum: General Help
---

### Post by northwestern on 2013-01-17
I have tried to run Ubuntu 12.10 from an external drive on my new Samsung laptop (Windows 8) without success. I have had to restore my computer three times and have decided enough is enough, until I can find a way and the confidance to try again.
I have the Ubuntu ISO on a pen drive and I use this to intall onto my external drive. The pen drive loads as normal giving the option of trying or installing Ubuntu. Trying ubuntu works very well and after shut down and removing the pen drive Windows loads as normal.
My question is this?
Would it be possible to load the ISO onto my external drive and use this as my second OS.
Is it possible to make:
a) Any changes I make permanent (at the moment all changes are lost).
b) Download all software updates as nomal.
c) Expand my external drive to accept any software I want to down load.
The drive I am using is 500 gb formatted to NTFS.

Regards
Northwestern

---

### Post by jim_deadlock on 2013-01-17
Run Ubuntu from your pen drive as usual (in Try mode). Run the Gparted app and shrink your external ntfs partition to make space for your Ubuntu installation (it will not install on ntfs).

Once you've made a space you should have a grey unallocated area on your external drive (as viewed in Gparted). You can either create a new ext4 partition on the drive at this point, or else just allow the Ubuntu installation to do it for you (in the next step).

From your pen drive, run the Install Ubuntu app on your desktop. When you get to the part where it prompts you where to install, select "something else". You need to put the boot loader (GRUB) onto your external drive (note: I think this has been your problem before, you keep zapping your Windows boot loader), and install Ubuntu on your new unformatted/ext4 partition.

This is a simplified explanation but it should get you going in the right direction. Once you've installed Ubuntu onto your external drive you need to make sure your BIOS is booting it, which you've probably already worked out. You should now have a fully installed and working Ubuntu installation on your USB drive.

---

### Post by northwestern on 2013-01-17
Thank for your reply.
My old laptop which was Windows 7 with BIOS, my new laptop (Samsung) came with Windows 8 which uses UEFI (not the normal BIOS) , even though in the last three occasions I have put the grub onto the external drive, on restart my MBR is corrupted forcing me to recover Windows 8.
Is there a way of converting the "try Ubuntu" mode into a system that I can use as normal.
Regards
Northwestern

---

### Post by oldfred on 2013-01-17
Because it is Windows 8, you need to boot install pen drive in UEFI mode to install to external in UEFI mode. External then needs to be gpt partitioned. Is it?

And first partition should be efi but it can be second if near beginning of drive, but if you already have a large NTFS that may be a problem. 

You may be able to install in BIOS/MBR mode, but then every time you want to reboot you have to go into UEFI/BIOS change from or to UEFI or BIOS and choose to boot. You are not able to easily dual boot one install in UEFI mode and one install in BIOS mode. Both really need to be installed in same mode.

                  UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by jim_deadlock on 2013-01-17
@oldfred just a quick question of my own, will a GPT-formatted drive boot normally on an older BIOS-based computer?

Edit: a bit of googling tells me a 32-bit system won't boot GPT.

---

### Post by oldfred on 2013-01-17
Windows will only boot from gpt with UEFI.

I am using gpt with my old BIOS based computers. I have gpt on an old 160GB drive, my now year old SSD & even on a flash drive to see if it worked and it does. 

With BIOS and gpt you have to have a tiny 1MB bios_grub unformatted partition to get grub to install correctly. After that I have not noticed any difference with system.

Have not tried 32bit as my 6 year old systems are both dual core Intel and work with 64 bit.

---

### Post by northwestern on 2013-01-17
Thanks for replies.
The Ubuntu 12.10 iso was transfered to my external drive using the universal boot installer (Pendrivelinux), I presume it loads in EFI mode (Secure boot still enabled). With the computer shut down in insert the external drive, the machine then boots up just like my old system did except the option are different, try or install. When I use the tey option it works perfectly, but, any changes I make are lost when I shut down.
Is there any way I can get to keep the changes.
Regards 
Northwestern

---

### Post by oldfred on 2013-01-17
If you are in the live Flash you have to turn persistence on to be able to save anything to the flash drive. It is not a full install and you cannot save full upgrades.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

   [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

