---
title: "Hacking up Apple print drivers for Ubuntu"
date: 2007-05-13
forum: General Help
---

### Post by aidanlister on 2007-05-13
I haven't been able to find any resources on this, so I set about doing this myself.

My printer is a DocuPrint 203A from Fuji Xerox. The default print drivers that come with Feisty print page-by-page, rather than all at once. I.e. The printer warms up, prints the page, them warms down. Rinse and repeat.

I found the OSX version of the print drivers on the product website. I tried mounting the .dmg file with:
$ mount -t hfs -o loop driver.dmg /mnt/driver
but it failed. It's not a HFS, as confirmed by:
$ file driver.dmg

I stuck the .dmg file onto my mac, and extracted the .pkg file, then put that back on my ubuntu computer.

The .pkg file is actually a folder, and I was able to open and peruse it without problem. The largest file was Archive.pax which I extracted with:

$ sudo aptitude install pax
$ pax -r < Archive.pax

This gave me a Printers folder. This folder contained "PPDs" and "FujiXerox". "PPDs" contained a "Contents" then "Resources" which contained a number of locales, selecting my language "en.lproj" I found "FX DocuPrint 203A CUPS.gz"

Renaming that file to .ppd.gz let me install it with the Add Printer stuff in Feisty. A win!

Unfortunately that didn't work at all. "Print test page" printed nothing.

The CUPS file makes reference to files that would be installed on a Mac:
*cupsFilter: "application/vnd.cups-raster 0 /Library/Printers/FujiXerox/Filter/rastertodp203a_204a"
*APDialogExtension: "/Library/Printers/FujiXerox/PDEs/FXNZLQuality04.plugin"
*APPrinterIconPath: "/Library/Printers/FujiXerox/Icons/FXNDP203A_204A.icns"

All these files exist in the Archive.pax but I'm guessing they are only usable within the mac context...

Has antone else had success with this? (I have attached the .pax, renamed to .bz2).

---

### Post by aidanlister on 2007-05-14
Any advice here?

---

### Post by Shazaam on 2007-05-14
I found a post that might help temporarily for you...
[http://ubuntuforums.org/showthread.php?t=273489](http://ubuntuforums.org/showthread.php?t=273489)

---

### Post by aidanlister on 2007-05-14
Hi Shazamm,

I am currently using the drivers suggested in that thread, so that was useful, but I'm keen to get a proper set working. It's a popular printer and I'm sure people would appreciate it.

---

