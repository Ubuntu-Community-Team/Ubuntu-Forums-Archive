---
title: "New to Ubuntu need help"
date: 2015-12-11
forum: General Help
---

### Post by lwilkovich on 2015-12-11
New to Ubuntu, I got this error and I have no clue.  It says Windows is hibernated but I don't think it is.

[IMG]https://sc-cdn.scaleengine.net/i/8475d1b08e116d0b3c6fea606889d606.jpg[/IMG]

Any help is appreciated.

Thanks,
Logan

---

### Post by dellboy56 on 2015-12-12
Hi there you probably have another hard drive i guess are you dualbooting? Is ubuntu your main os? If your dualbooting then that why ubuntu cant see it because it cant read NTFS and cant mount the files correctly

---

### Post by Bucky Ball on 2015-12-12
*Thread moved to **Installation & Upgrades**.*

> **dellboy56 said:**
> Hi there you probably have another hard drive i guess are you dualbooting? Is ubuntu your main os? If your dualbooting then that why ubuntu cant see it because it cant read NTFS and cant mount the files correctly

??? Ubuntu sees, mounts, reads and writes to NTFS just fine so not sure where you got this information. :-k Little to do with this as the Windows partition is completely inaccessible, i.e. hibernating. The error message confirms this. 

> Windows is hibernating. Refuses to mount.

Regardless of whether Ubuntu reads/writes NTFS, it would still show the NTFS partitions, which it isn't.

@lwilkovich: Welcome. Yes, Windows IS in hibernating. That is probably the reason you are getting that message. Boot to Windows, switch off hibernate and faststart and SHUTDOWN the Windows install completely. Switch the machine off. Then, boot to the BIOS and switch off secureboot and make sure, if Windows is installed in UEFI, you install Ubuntu in UEFI. Use the 'Something Else' option when you get to partitioning. If you've done all that, simply boot to Windows and switch off hibernate and faststart, reboot and then see if you can access from Ubuntu.

It is not a good idea to be accessing and changing files in the Windows OS partition from Ubuntu in any case. This can be problematic and screw the Windows install. You should create a shared NTFS partition for sharing data between the two OSs. In other words, you should avoid mounting the Windows OS partition in Ubuntu in the first place. 

PS: Please spare a thought for those with slow connections and/or vision issues and attach large pics using 'Go Advanced' or 'Adv Reply' and using the paperclip icon in the toolbar there. Thanks. :)

---

