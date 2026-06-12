---
title: "problem with Wubi minefield 179.52"
date: 2007-06-07
forum: General Help
---

### Post by MikeM709 on 2007-06-07
when i tried to install wubi, all went well until it went to create the virtual disks. what happened is i get stuck at about 70% for forever.
i am testing the minefields on Vista and it normally goes much faster. at least with previous minefields.

[img]http://img72.imageshack.us/img72/633/wubi17952stuckwi1.th.jpg[/img]

---

### Post by ago on 2007-06-07
yep that is slower but it should finish within a few minutes.

---

### Post by MikeM709 on 2007-06-07
i let it go for like 20 then i thought some thing was wrong so i killed the process and then deleted the folders by selecting to uninstall it and then tried a second time but the same thing happened. i know computers can sometimes take a long time, but i mean like 20 minutes+ for something that took less than a minute before seemed kind of wrong to me. i'll give it another go though.

---

### Post by ago on 2007-06-07
At the moment it is zeroing the full file, so it means that it has to write #GB. If you choose a small size it will help.

---

### Post by MikeM709 on 2007-06-07
i chose ten GB before you made that post so i guess i'll just wait it out. i think im gonna go browse you tube or something while im waiting.

---

### Post by MikeM709 on 2007-06-07
ok i watched a few youtube vids while waiting and it eventually finished so i restarted but i got 3 options to boot.

Windows Vista
Wubi Ubuntu
Ubuntu

when i tried the Wubi ubuntu one i get the following message:
```

     File: wubi\boot\winboot\wubildr.mbr

     Status: 0xc000000d

     Info: The selected entry could not be loaded because the application is missing or corrupt.
```

And when I try the Ubuntu one i get this message:

```
     File: \wubildr

     Status: 0xc000007b

     Info: The selected entry could not be loaded because the application is missing or corrupt.
```

All this happens after wubi finishes and askes me to reboot. i select reboot now and then when it comes back this happens.

---

### Post by Spegelius on 2007-06-08
Could you run 'bcdedit' in command prompt (with Admininistrator rights) and post the output? I had some problems with bcd items wubibcd created (didn't have time to test thoroughly).

Oh and also could you tell where Wubi is installed (c: or other drive)

---

### Post by ago on 2007-06-08
It might also be an issue with wubildr.mbr. Try the following:

download [http://download.gna.org/grub4dos/grub4dos-0.4.3-2007-06-06.zip](http://download.gna.org/grub4dos/grub4dos-0.4.3-2007-06-06.zip)

extract into boot drive, rename grldr.mbr -> wubildr.mbr, then copy menu.lst from c:\wubi\boot\winboot\menu.lst to c:\

---

