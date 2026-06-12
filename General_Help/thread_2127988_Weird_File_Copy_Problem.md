---
title: "Weird File Copy Problem"
date: 2013-03-21
forum: General Help
---

### Post by nonedrinkwater on 2013-03-21
I'm trying to copy a file from an ubuntu netbook running 12.04 64bit, to a flash drive that is formatted to NTFS, I tried using fat32 but the file is 5gigs, and it doesnt support that file size, so NTFS is my only option. (or is it? please correct me if im wrong) 

The flash drive is 8gb, is there a limit has to how big files can be, when transferred from ubuntu to windows 7? 

also... i tried to share a folder on windows7 over the network, so that i can copy the file directly from the netbook to the windows 7 machine through my router, but after 4 gigs it stops..... what am i doing wrong here?

---

### Post by ManamiVixen on 2013-03-21
fat16 has a limit of 4Gb, fat32 is up to 500Gb I believe. So fat32 is fine.

---

### Post by slickymaster on 2013-03-21
With FAT32, the maximum file size is 4.3GB.

A possible solution you can approach is to split the original file in 5 smaller ones of 1GB each:
```
split -b 1GB -d Largefilename Smallfilename
```
That line will create five smaller files, with 1GB each:
Smallfilename00
Smallfilename01
Smallfilename02
Smallfilename03
Smallfilename04

Afterwards you just have to join then in the windows machine:
```
copy/b Smallfilename00+Smallfilename01+Smallfilename02+Smallfilename03+Smallfilename04 Largefilename
```

See ```
man split
```for help.

---

### Post by nonedrinkwater on 2013-03-24
thank you sir. =)

---

