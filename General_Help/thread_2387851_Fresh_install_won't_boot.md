---
title: "Fresh install won't boot"
date: 2018-03-24
forum: General Help
---

### Post by dryan775 on 2018-03-24
Hello all,

My hard drive has given me a bunch of problems, so I decided to replace it.
About an hour ago, my new WD 750GB drive arrived and I installed it (bare)

Loaded Ubuntu 16.04.2 LTS from a USB stick and went through installation.  It said everything was fine. 
Removed the USB, rebooted.

Got this error: 
Reboot and select proper boot device
or install boot media in selected boot device and press a key.

Rebooted into live with USB and ran Boot-Repair.  It seemed to think it had fixed it.
Rebooted again with USB removed.  Same error.

Rebooted into live with USB again, reran Boot-Repair.
Here is the pastebin.

[http://paste.ubuntu.com/p/8kHrdt86dX/](http://paste.ubuntu.com/p/8kHrdt86dX/)

Not sure what i'm doing wrong.  This laptop has been running 16.04 for nearly 2 years before the old drive started to go, so I don't think it's a hardware issue.  The Disks app in the stock build shows a 537MB FAT32 EFI, filesystem, and swap partitions, so the drive appears ot be compatible with this machine.

Thanks in advance for any help!

  DwR

---

### Post by yancek on 2018-03-24
Are you going into the BIOS and changing the settings for boot priority and selecting the internal drive as suggested in boot repair?  You appear to have the correct EFI files for Ubuntu and other boot files on the Ubuntu partition.  Check to see if you have an option to boot from EFI file in boot options, navigate to the Ubuntu directory in EFI.

---

### Post by dryan775 on 2018-03-24
I'm kinda new at this and not sure how to even access the EFI files since I can only mount the one large partition once in the Live session.

I did confirm that the system setup (entered by pressing F12 during the Toshiba splash screen) does have the HDD as the first boot option, USB was not inserted at boot.
BIOS password is off
Secure boot is disabled

I didn't see it before, but it did flash this message by fairly quickly:
Failed to open \EFI\BOOT\grubx64.efi - Not Found
Failed to load Image \EFI\BOOT\grubx64.efi:  Not Found
start_image() returned Not Found

System is a Toshibs C55-B5356
Intel i5, 8GB, drive is a new, bare 750 WesternDigital

Quote:
Check to see if you have an option to boot from EFI file in boot options, navigate to the Ubuntu directory in EFI.

Not sure HOW to do this part.

Thanks
   DwR

---

### Post by dryan775 on 2018-03-24
Screenshots of my System settings screens:

[https://drive.google.com/drive/folders/1Uw2a5DGEnloZOiBCrSnR2JR-r3NWqQ5-](https://drive.google.com/drive/folders/1Uw2a5DGEnloZOiBCrSnR2JR-r3NWqQ5-)

---

### Post by yancek on 2018-03-24
> Failed to open \EFI\BOOT\grubx64.efi - Not Found
Failed to load Image \EFI\BOOT\grubx64.efi:  Not Found

I don't know why it is looking for those files.  You get the message because neither file exists in that location but boot repair shows the grubx64.efi file is in /EFI/ubuntu.  Do you get a grub prompt at boot (grub>)?  If not what do you see?  If you see the grub prompt or if you see the grub menu, hit the c key to get a grub prompt and from there, enter each of the lines below, hit the Enter key after each and see if it boots.  If you don't see the grub menu on boot, try holding or tapping the shift key as soon as it begins to boot. 

> insmod part_gpt
insmod fat
set root='hd0,gpt1'
chainloader /EFI/ubuntu/grubx64.efi boot

---

### Post by dryan775 on 2018-03-24
I do not get a grub menu.  

After the Toshiba splash screen, the "Failed to open \EFI\BOOT\grubx64.efi - Not Found" flashes by fairly quickly, 
The screen then clears and all I get is the:

Reboot and select proper boot device
or install boot media in selected boot device and press a key.

Is there a way to edit the file path to where my EFI files ARE located from a Live session?

---

### Post by yancek on 2018-03-24
After you see the Toshiba splash screen, hold down the shift key.  The process is explained in detail in the Ubuntu documentation at the site below.  You should select the Advanced options as explained and you do have it as it is shown in the output of your boot repair in the grub.cfg file.

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by oldfred on 2018-03-24
Have seen that error before and it does not make sense.
An UEFI fallback or hard drive entry uses /EFI/Boot/bootx64.efi.
And an Ubuntu entry users either /EFI/ubuntu/grubx64.efi or /EFI/ubuntu/shimx64.efi.

But their is no correct path in /EFI/Boot for grubx64.efi.

Boot-Repair does copy shimx64.efi to /EFI/Boot/bootx64.efi and rename it. That is often required as a fallback boot entry or hard drive boot entry. (And UEFI ubuntu entry probably does not work).

If only booting Ubuntu and not Windows another work around is this. Boot-Repair used to do this, but those dual booting would have a Windows update overwrite the entry.

       **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

And then boot the "Windows" UEFI boot entry in UEFI menu.

---

### Post by dryan775 on 2018-03-25
After response #7 (I didn't see #8 until after I did this):

Tried the shift thing, absolutely no effect, I can't get to grub.  
I found a way to mount it and did an ls to confirm the grubx64.efi file is not there, named bootx64.efi  (just as #8 says)

Rebooted into Live session and used boot repair to purge and reinstall grub.  
Got an updated pastebin in case this doesn't work:
[http://paste.ubuntu.com/p/PhHTQGcQzc/](http://paste.ubuntu.com/p/PhHTQGcQzc/)


About to shut down again and try this.

---

### Post by dryan775 on 2018-03-25
Nope, still won't boot.
Still get the splash screen, then 

Reboot and select proper Boot device
or Insert Boot Media in selected Boot device and press a key.

---

### Post by dryan775 on 2018-03-25
Poking around on the /mnt/EFI folder, there is a Boot folder (not sure if this is case sentative) and a ubuntu folder

Looks like it it looking in the boot folder, but the file it wants is in the ubuntu folder.  Can I just move that file, or rename the folders so the file it is looking for is in the path that it wants?

---

### Post by dryan775 on 2018-03-25
OK, the simple solution seems to be the one that worked.

I simply mounted the sda0 as a drive, navigated to it's structure and copied the file it was looking for from the /EFI/ubuntu folder to the /EFI/Boot folder.

Works.

---

### Post by oldfred on 2018-03-25
Very stange, but whatever works.
Will add this thread to notes on Toshiba issues.

I believe Toshiba is now one of those systems that violates UEFI standards, but seems to be a bit different in what actually will or can work.

---

