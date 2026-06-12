---
title: "UEFI: Just installed Ubuntu and wont boot"
date: 2014-01-30
forum: General Help
---

### Post by dafinder on 2014-01-30
I've been at this for HOURS and I can't figure it out. I've done everything I can think of, deleted all partitions and let Ubuntu do it's thing automatically. 

I just ran Boot Repair and still nothing. It just hangs with nothing happening.

This is from Boot Repair.

[http://paste.ubuntu.com/6844004/](http://paste.ubuntu.com/6844004/)

Can someone help me??

It tells me to do something with EFI in my BIOS. However, I can't see anything in my BIOS. I can see UEFI support for USB but not for a Harddrive. 



I can boot from a liveusb but nothing without it. No grub, nada. 
Thanks!

---

### Post by buzzingrobot on 2014-01-30
Does your BIOS offer an option to choose which drive to boot from? 

Remove the USB. Reboot and enter the BIOS. Choose the drive that corresponds to /dev/sda as the boot drive. Save and reboot. Cross fingers.

---

### Post by dafinder on 2014-01-30
Tried and nada

---

### Post by oldfred on 2014-01-30
With one system, you normally do not get grub menu. You have to hold shift key from BIOS until menu appears. With some UEFI system you have to hit escape key to get grub menu. 

What computer is this? Some are hard coded in UEFI to only boot Windows. The work around is to rename grub/shim to have Windows efi file name. 

       Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries
Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)


Some UEFI screens.

---

### Post by dafinder on 2014-01-30
Its an Asus k52 I had kubuntu running on it with another hdd but tried installing windows and screwed something up.

---

### Post by dafinder on 2014-01-30
Did the boot repair say anything useful?

---

### Post by oldfred on 2014-01-30
Boot-Repair looks normal but it says 13.04

 EOL Notice: Raring (13.04) will be End of Life on January 27, 2014
[http://releases.ubuntu.com/13.04/](http://releases.ubuntu.com/13.04/)

So you will not get any updates or fixes.

---

### Post by dafinder on 2014-01-30
I d/l it because it came with bootrepair, but every distribution I've tried wont boot. When I installed my kubuntu distribution I did not install it uefi but legacy.so I'm not sure what is going wrong.

---

### Post by Bucky Ball on 2014-01-30
January 31st here so it's gone. I would install 12.04 LTS or 13.10 instead. Both are directly upgradeable to the five year supported 14.04 LTS due in April.

---

### Post by dafinder on 2014-01-30
Is there a 12.04 distribution with boot repair included

---

### Post by Bucky Ball on 2014-01-30
No. Not unless there's an obscure home-made hybrid spin or something else I don't know about. You can install it in Ubuntu. You can even install it when you are running from install media and not a hard drive install (but you must be onlines). You can also boot it live from install media.

---

### Post by dafinder on 2014-01-30
Ok ill get on it. Any ideas on why its not booting at all

---

### Post by oldfred on 2014-01-30
You can download any Ubuntu install version and add Boot-Repair. If not a flash drive with persistence, you do have to re-download on every reboot, but it is not a large application.

Was this originally Windows 7? If so it may have an early version of UEFI from the vendor and needs update or just install in BIOS mode. You can use BIOS with gpt partitioning. I like to leave an efi partition at beginning of drive in case you want to convert to UEFI later, but with BIOS boot you need a small 1 or 2MB unformatted partition with the bios_grub boot flag, otherwise grub will not install in BIOS boot mode correctly.

---

### Post by waterhead on 2014-01-30
I don't know if your problem is the same as the one I had.

I installed Ubuntu on my Toshiba U925t, and the install seemed OK. But when I booted after the install, I got an error telling me to insert a boot disk and press enter! For a fraction of a second, before the error message, I saw this:

Could not open "\EFI\BOOT\fallback.efi"

Following advice found in this [bug report](https://bugs.launchpad.net/ubuntu/+bug/1241824), I booted again from the install image . I then copied this file:

/boot/efi/EFI/ubuntu/grubx64.efi

And pasted it as "fallback.efi":

/boot/efi/EFI/Boot/fallback.efi

---

