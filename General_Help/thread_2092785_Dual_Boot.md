---
title: "Dual Boot"
date: 2012-12-08
forum: General Help
---

### Post by mountainman70 on 2012-12-08
I have a Optiplex 745 with XP SP3 installed on the 80 gig hdd sata drive.
I have a 80 gig ide hdd with Ubuntu installed that I was using as an external drive on another computer.

How do I get the 745 to recognize the external ide hdd and give me the option to boot either XP or Ubuntu?

---

### Post by Herman on 2012-12-09
I don't know anything about Optiplex 745's in particular, but with most computers if you want to get them to boot from a non-first HDD you can do it most easily from the bios boot menu.
To bring up the bios boot menu, you turn the computer on and then press a key during the early stages of booting. Exactly which key will bring up your motherboard's bios boot menu will need to be found out either by reading your motherboard manual or by trial and error. Likely candidates are F12, F8 or F1, but it could be any key.  The bios boot menu should give you a list of drives you can choose from. Select the one you want and boot.

---

### Post by johnycsf on 2012-12-09
A lot of times if the OS is already loaded into the HDD specially if it was used with another computer. Then new computer will not recognize it because it is different. 
In other words if any hardware is different if you get lucky enough for the system to recognize it, you will have problems during boot.
My suggestion is to save whatever you can from that hdd into a usb and re-install the OS while plugged to the new computer!

Hope it helps!

---

### Post by Bucky Ball on 2012-12-09
As Herman says, change the boot order in BIOS to boot from the external HDD. Obviously, it will need to be plugged in and switched on.

I see no real reason to wipe the drive and start again ...

---

### Post by mountainman70 on 2012-12-09
> **Bucky Ball said:**
> As Herman says, change the boot order in BIOS to boot from the external HDD. Obviously, it will need to be plugged in and switched on.

I see no real reason to wipe the drive and start again ...
Thanks for the input. Tried changing the settings in bios but made no difference.
I believe because external is IDE and computer is SATA I will have to get a SATA HDD and install Ubuntu on it.

---

### Post by Bucky Ball on 2012-12-09
The hard disk is IDE but is it in an external case? If so, how is this plugged in? USB? In this case it doesn't really matter whether it's IDE or SATA. The machine sees it as a USB device.

If you have taken the external drive out of the case and put it in the machine, perhaps Ubuntu is not installed properly, BIOS is checking out that drive first, finding nothing it recognises to boot, so moving on to the next HDD or optical drive on the list.

It should make no difference whatever whether you have Ubuntu on an IDE or SATA drive. That is not your problem so look elsewhere (and save your money). I have Ubuntu booting from an IDE in the desktop faultlessly and have had for five years or more ...

---

### Post by mountainman70 on 2012-12-09
[QUOTE=Bucky Ball;12396489]The hard disk is IDE but is it in an external case?

(The hard disk is IDE but is it in an external case?)

YES Hdd is IDE and in external case.

 (If so, how is this plugged in? USB?) 

YES.

(If you have taken the external drive out of the case and put it in the machine, perhaps Ubuntu is not installed properly.)

Have not put it in machine as I don't have a SATA to IDE connector and I don't see an IDE connection. Came from another computer using IDE.
Will try bios again. 

Thanks>

---

### Post by Mark Phelps on 2012-12-10
You've got a couple of problems to deal with ...

You mentioned using SATA-to-IDE connector to try to boot internally from the IDE drive.  I tried that on a new PC, as the motherboard had no IDE ports, and I tried several different kinds of adapters -- and NONE of them would boot.  Once I booted from a SATA drive, I could SEE the IDE drive, but I could not boot from it.

Also, if you were using the drive externally, you were probably NOT booting from it, which in the case of Ubuntu, means you probably had not installed GRUB to it.  You would need GRUB installed to it to boot into Ubuntu.

---

### Post by mountainman70 on 2012-12-11
> **Mark Phelps said:**
> You've got a couple of problems to deal with ...

You mentioned using SATA-to-IDE connector to try to boot internally from the IDE drive.  I tried that on a new PC, as the motherboard had no IDE ports, and I tried several different kinds of adapters -- and NONE of them would boot.  Once I booted from a SATA drive, I could SEE the IDE drive, but I could not boot from it.

Also, if you were using the drive externally, you were probably NOT booting from it, which in the case of Ubuntu, means you probably had not installed GRUB to it.  You would need GRUB installed to it to boot into Ubuntu.

IDE drive with Ubuntu would boot from old IDE computer as Master or as external using Boot floppy. I can not see it as external in the Dell 745 and there is no floppy drive so I can only use the USB port.
So I am not sure what you mean by needing to install Grub. Wouldn't it already be on the IDE drive? Still trying to learn about Linux.
Thanks.

---

### Post by Mark Phelps on 2012-12-11
Yeah ... missed the part where you said "with Ubuntu installed". So, you WOULD already have GRUB installed.

---

### Post by mountainman70 on 2012-12-14
> **Mark Phelps said:**
> Yeah ... missed the part where you said "with Ubuntu installed". So, you WOULD already have GRUB installed.

I thought I would bring you up to date. I remembered that I had a pipbt.iso cd that I had made to go along with my floppy. I put it in the dvd rom and booted up and it started and brought up the grub screen and I clicked on the grub kernel and it then went to "Press any key" which I get when I use the floppy on the Gateway. But on this Dell Optiplex 745 it just hangs there. I tried 3 Ubuntu drives and get the same results.

---

