---
title: "How to make built in SD Memory card work under Feisty 7.04"
date: 2007-04-29
forum: General Help
---

### Post by llib1234 on 2007-04-29
I followed this guide and it worked perfectly! [COLOR="DarkOrange"]http://ubuntulinuxtipstricks.blogspot.com/2007/04/texas-instruments-sdmmc-card-reader.html[/COLOR]

Basically, download the TIFM installer/script from this site, extract it, and run it in terminal mode. All compiling is automatic. However, use this command to get the compiling tools beforehand if you have never compiled on your current system before: **sudo aptitude install build-essential linux-headers-`uname -r`** (Copy and paste the preceding command into your Terminal and press Enter. This will download the compiling tools for you. Then run the TIFM installer)

Restart your system and insert a SD or MMC card to see if it works for you.

(My internal card reader is made by Texas Instrument.)

---

