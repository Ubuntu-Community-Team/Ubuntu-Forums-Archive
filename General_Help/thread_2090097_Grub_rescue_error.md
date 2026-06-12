---
title: "Grub rescue error"
date: 2012-12-01
forum: General Help
---

### Post by teddy379 on 2012-12-01
So I deleted the Ubuntu partition and I'm bot able to log into Windows 7 any more. I tried every possible fix including:
1- Win7 Disc, repair > bootrec /fixmbr and /fixboot
2- bcdedit/export C:\BCD_Backup
C:
CD Boot
Attrib bcd -s -h -r
ren C:\boot\bcd bcd.old
bootrec /rebuildBCD
3- Using the built-in repair in Win7 Disc.
4- Logging into Windows 7 and using the EasyBCD program.
5- bootsect /nt60 SYS and ALL

And yea, if you're wondering how I managed to log onto Windows 7, well, the only way was setting the primary boot device from the BIOS to "CD-ROM" and ignoring the Win7 Disc when it asks me to press a key to use the disc.

So yea, how do I get rid of the missing Grub stuff?

---

### Post by kiyop on 2012-12-01
Do you know if your computer uses UEFI, RAID, encryption, GPT?
Can you post the settings in BIOS?

Can you boot linux live CD/DVD/USB and execute boot info script and post the contents of the generated RESULTS.txt?
Please wrap the contents (text) by "[ code]" and "[ /code]" tags (please omit the spaces just after "[").
You can download boot info script at [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

