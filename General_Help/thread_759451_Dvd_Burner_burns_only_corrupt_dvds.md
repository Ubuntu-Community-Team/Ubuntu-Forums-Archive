---
title: "Dvd Burner burns only corrupt dvds"
date: 2008-04-19
forum: General Help
---

### Post by zarqoon on 2008-04-19
I've a very weird problem with my dvd burner. Every time i burn a cd or dvd with ubuntu it will not be fully readable. Some files will work others will report crc errors. I tried several different programs to do this and it does not make a difference. 
Naturally i would think the burner is going to get old, but the weird thing is if i boot windows and burn a dvd it will work perfectly and in the time i used windows before i switched it almost never screwed up. 
I've a Plextor Px-716A by the way

This is the output of dmesg | grep hdc
```

[   41.519110]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[   42.906080] hdc: PLEXTOR DVDR PX-716A, ATAPI CD/DVD-ROM drive
[   48.938301] hdc: ATAPI 126X DVD-ROM DVD-R CD-R/RW drive, 8192kB Cache, UDMA(66)

```

---

### Post by TenPlus1 on 2008-04-19
If you are using Brasero to burn your dvd's, make sure Windows compatibility is checked and you burn at lower speeds if discs are becoming corrupt... This will help...

---

### Post by zarqoon on 2008-04-19
I am not. But i cant read the discs with ubuntu either. They will just be corrupt.
If i burn using windows i can read the discs. My ps2 wont read discs that i burn with ubuntu either.
And as to speed i already tried doing 2x burns which is the slowest my burner will do. Using win even 16x will work most times.

---

### Post by ramjet_1953 on 2008-04-19
What package are you using to burn the disks?

Regards,
Roger :cool:

---

### Post by zarqoon on 2008-04-20
I am not exactly sure what you mean by package. I tried gnomebaker and k3b both installed via the add/remove applications manager. I also tried using growisofs from a command prompt. 
```
 
growisofs --version
* growisofs by <appro@fy.chalmers.se>, version 7.0.1,
  front-ending to genisoimage: genisoimage 1.1.6 (Linux)

```

And i tried clicking the write to disc using the context menu for an iso in nautilus.

---

