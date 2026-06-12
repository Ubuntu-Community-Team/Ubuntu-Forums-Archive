---
title: "BIOS Update for HP Compaq 6910p"
date: 2021-04-05
forum: General Help
---

### Post by GhX6GZMB on 2021-04-05
I possess two of the mentioned laptops (2008/2009 vintage), both were unfortunately born with Win Vista. They are now running Lubuntu 20.04.2.

I'd like to upgrade the BIOS on both machines, but am unsure about how to do this. The HP support site has the updated BIOS files available, but only as .exe files.

Is there a smart way here? Bringing the machines back to Vista is out of the question, but I've wondered if a Wine installation could help?

Any tips and tricks are very welcome.

Thank You.

---

### Post by CatKiller on 2021-04-05
> **ml9104 said:**
> I'd like to upgrade the BIOS on both machines, but am unsure about how to do this. The HP support site has the updated BIOS files available, but only as .exe files. 
UEFI can generally read the files needed to update it itself. Stick it on a USB stick (probably formatted with FAT), boot into the setup, and see. HP do sometimes have very peculiar implementations, though. 

> Bringing the machines back to Vista is out of the question, but I've wondered if a Wine installation could help?
It wouldn't.

---

### Post by GhX6GZMB on 2021-04-05
Thanks, so Wine is out.
But these are not UEFI machines, only BIOS. I can try to run the .exe files on my Win machine to see if they unpack somehow, but am afraid to brick somthing.

Are there other utilities available?

---

### Post by CelticWarrior on 2021-04-05
[https://support.hp.com/sk-en/document/c00042629](https://support.hp.com/sk-en/document/c00042629)

---

### Post by GhX6GZMB on 2021-04-05
Thank You, but that doesn't work either. Again: these laptops are pure BIOS, no UEFI available. The link to support.hp.com presumes UEFI.
I know these laptops are old, but they have the best keyboards and are damn fast. I'd like to keep them alive.

I've toyed with the idea of a Vista "live boot" DVD, but that won't fly either...

---

### Post by CatKiller on 2021-04-05
> **ml9104 said:**
> I've toyed with the idea of a Vista "live boot" DVD, but that won't fly either...

It wouldn't be Vista that you'd use. If your BIOS is actually incapable of updating itself, which you don't appear to have tried, it would be a DOS boot disk that you'd be making, and the executable that you downloaded would simply be a utility to create one.

---

### Post by Frogs Hair on 2021-04-05
I have a later model of that computer which came with Win 7 and there was HP software that performed the actual bios update. Downloading the .exe was done through the HP update utility in the desktop environment. That may be different on earlier models.

---

### Post by GhX6GZMB on 2021-04-05
> [COLOR=#000000]If your BIOS is actually incapable of updating itself, which you don't appear to have tried,[/COLOR]

Nasty comment and inappropriate. I've tried all combinations of Fx keys, Esc etc. to get to a BIOS menu that will allow an update. No cigar.
The link from Celtic was good, but apparently related to later laptops with UEFI features (yes, I tried it).

> [COLOR=#000000]there was HP software that performed the actual bios update. Downloading the .exe was done through the HP update utility in the desktop environment.[/COLOR]

Yes, well... this is a Lubuntu laptop that does not run HP/Windows software.

---

### Post by Frogs Hair on 2021-04-05
> **ml9104 said:**
> Nasty comment and inappropriate. I've tried all combinations of Fx keys, Esc etc. to get to a BIOS menu that will allow an update. No cigar.
The link from Celtic was good, but apparently related to later laptops with UEFI features (yes, I tried it).



Yes, well... this is a Lubuntu laptop that does not run HP/Windows software.

I'm aware you want to update with an .exe on Linux . I _was _able to update my bios to the final version while dual booting, but with a supported version of Windows.

---

### Post by mikewhatever on 2021-04-05
You need to use Windows or FreeDos. There is no magic way to run an exe BISO update on Ubuntu. It is not a nasty comment, it is reality.

---

### Post by CelticWarrior on 2021-04-06
> **mikewhatever said:**
> You need to use Windows or FreeDos. There is no magic way to run an exe BISO update on Ubuntu. It is not a nasty comment, it is reality.

But the link I posted above suggests one way outside Windows. Its own executable BIOS/UEFI updater can be used from another Windows computer to make a USB bootable firmware updater media. What does it run underneath I don't know but I guess it's FreeDOS.

For new UEFI HPs that can update the firmware from inside the settings it's just a matter a extracting the .exe with 7Zip (Windows or Linux) and copy the BIN file to the root of a standard FAT32 USB stick.

For old BIOS the USB bootable media is probably the best option.

---

### Post by ActionParsnip on 2021-04-06
+1 for freedos

---

### Post by GhX6GZMB on 2021-04-07
Thank You for your suggestions.
I think I'll let this issue rest for a while, it's not urgent, the laptops run.
FreeDOS is probably the way to go, but the documentation on how to make a bootable USB/DVD is so miserable that I've been scared off.

Thanks again.

---

### Post by CelticWarrior on 2021-04-07
> [COLOR=#000000]FreeDOS is probably the way to go, but the documentation on how to make a bootable USB/DVD is so miserable that I've been scared off.[/COLOR]

The documentation is in the HP link I posted before.
All you need is a Windows computer to run the installer and select the option to create a bootable USB. That's all.

---

### Post by GhX6GZMB on 2021-04-07
Thanks, CelticWarrior, but I tried that.
The HP driver file (sp39750.exe) simply extracts a handful of files, but does not create a bootable image. None of the options in the HP link appear.

It seems I need to manually create a FreeDOS bootable USB and then run the BIOS update from there.

---

### Post by GhX6GZMB on 2021-04-08
Final Update:
Project "update BIOS" is dead.
I made a live-boot DVD with FreeDOS, which boots beautifully (into an R: drive, which is somewhat weird).

I copied the sp39750.exe file onto a USB drive, which is recognized by FreeDOS, and tried to run it.
Error: "This program cannot be run in DOS mode."
OK, it's an archive, so I unpacked it and ran hpqrun.exe which is the main file from unpacking.
Same error.

No cigar. I'll live with the current BIOS versions.

Thanks.

---

