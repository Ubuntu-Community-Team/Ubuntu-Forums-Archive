---
title: "How Do I Get Into BIOS?"
date: 2020-09-03
forum: General Help
---

### Post by rbscairns on 2020-09-03
I recently replaced my old 32 bit PC with a new 64bit PC. This new PC had Windows 10 pre-installed. Windows 10 does not normally allow you to enter BIOS at startup. After a bit of study, I was able to boot into my live Lubuntu 20.04 DVD disk, delete Windows 10 and install Lubuntu 20.04.

Now when I boot my new PC I am still not allowed to enter BIOS at startup. Is there a way to enter BIOS from Lubuntu 20.04?

---

### Post by guiverc on 2020-09-03
I'm not aware of any OS stopping the user who boots it from going into UEFI/BIOS. Machines I've used have a key that when pressed enters setup mode after device is turned on, even on a key combination turns on the device and enters setup mode. I would double check your PC doesn't allow it.

However if you've still got your Lubuntu install media (I tested this just now with *groovy* and 20.04.1 install media) when I boot it I get the options to

 - Start Lubuntu
 - Start Lubuntu (safe graphics)
 - OEM install (for manufacturers)
 - Boot from next volume
 - UEFI Firmware Settings

I'd try the last option (UEFI Firmware Settings).

[I]Note: the options I list occurred on a number of boxes; but differed on older boxes for Lubuntu where UEFI wasn't enabled/used.
[/I]

---

### Post by CatKiller on 2020-09-03
On UEFI systems one can also use ```
systemctl reboot --firmware-setup
```

---

### Post by HermanAB on 2020-09-03
"systemctl reboot --firmware-setup" - Thanks for that tip!

---

### Post by crip720 on 2020-09-03
Most PCs have a key to press at start up to enter bios, use use google to find for yours.  Windows also has a way to enter bios by their troubleshooting page at startup also and grub has similar setting.  A simple google search containing your computer make and model will find this.

---

### Post by rbscairns on 2020-09-03
With my older PC, if I wanted to boot from a CD, I would enter the BIOS by pressing [Delete] during the boot sequence which would take me into BIOS where I could change the boot order so that the CD was the first tried. When I got this new PC with Windows pre-installed, this option was not available for booting from my Lubuntu live CD. I eventually found a way within Windows  to get the PC to boot from my Lubuntu live CD. From memory, that way included something about UEFI, so I probably have a UEFI system (whatever that is).

The Windows  OS is now deleted and I have only Lubuntu 20.04 installed. I just tried CatKiller's suggestion. I connected my external CD drive with the Lubuntu live CD and entered the code in terminal. My PC rebooted but into my installed OS and not the connected CD. I will now try various keys during the boot sequence to see if anything happens.

---

### Post by rbscairns on 2020-09-03
I have now found that I can get into BIOS by regularly pressing [Delete] during the boot process. That solves this problem but presents another problem.

In BIOS, I go to change the boot options so that the PC will boot from my external optical drive with live Lubuntu (as a trial). The boot options given are:

Boot Option #1 [ubuntu (PO: SSD128GBS800)]
Boot Option #2 [Windows Boot Manager]
Boot Option #3 [UEFI SlimtypeeTAU1082 LL07]
Boot Option #4 [ubuntu (PO: SSD128GBS800)]

The UEFI Slimtype is my external optical drive. I wanted to make that Boot Option #1. Unfortunately, the BIOS only allow me to swap option #1 with option #2 and swap option #3 with option #4. There does not appear to be a way of making my optical drive option #1.

I have decided to mark this thread [Solved] and start a new thread on my boot options problem later. I still have a printer problem in LibreOffice to work on and that is most important.

Thank you all for your guidance.

---

