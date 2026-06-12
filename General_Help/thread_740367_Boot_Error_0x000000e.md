---
title: "Boot Error 0x000000e"
date: 2008-03-30
forum: General Help
---

### Post by AussiMike on 2008-03-30
I have not been able to find a resolution to this problem in the forums so I was wondering if someone could please advise....

Installed latest WUBI kit on VISTA based server. Install goes fine but on re-boot if I select Ubuntu I get...

Windows Failure to start
File: \ubuntu\winboot\wubildr.mbr
Status: 0x000000e
Info: The selected entry could not be loaded because the file is missing or corrupt

Used EasyBCD to check boot loader and it looks fine to me......attached extract below

There are a total of 2 entries listed in the Vista Bootloader.
Bootloader Timeout: 10 seconds.
Default OS: Microsoft Windows Vista

Entry #1

Name:  Microsoft Windows Vista
BCD ID:  {current}
Drive:  C:\
Bootloader Path:  \Windows\system32\winload.exe
Windows Directory:  \Windows

Entry #2

Name:  Ubuntu
BCD ID:  {981de62c-fdf4-11dc-a006-0019d15b86ef}
Drive:  P:\
Bootloader Path:  \ubuntu\winboot\wubildr.mbr

---

### Post by ago on 2008-03-30
Try to copy all the files in C:\ubuntu\winboot to C:\
Then use easybcd to point to C:\wubildr.mbr

---

### Post by AussiMike on 2008-03-30
Thanks for the information...tried this and got the following error messages

try (HD0,0) NTF5: No Wubildr
try (HD0,1) invalid or null
try (HD0,2) invalid or null
etc...
then
Cannot find GRLDR in all devices

---

### Post by ago on 2008-03-30
Isn't there wubildr in c:\?

---

