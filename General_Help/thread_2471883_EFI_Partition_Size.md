---
title: "EFI Partition Size?"
date: 2022-02-11
forum: General Help
---

### Post by rsteinmetz70112 on 2022-02-11
I am replacing and updating the storage in one of my computers. I don't need it now but to preserve my options I intend to create an EFI partition to future proof the install. How big should I make it? I don't have any idea How I might use it in the future. I've seen statements the 100MB will work but 200 would be better and also recommendations for 550 MB.

---

### Post by &amp;KyT$0P# on 2022-02-11
512MB seems to be the standard size these days.  And it has been plenty big for me for *buntu-only single-boot systems (I don't dual boot).  According to [FONT=Courier New]df[/FONT] my primary system only use 2% of that.

---

### Post by yetimon_64 on 2022-02-11
> **halogen2 said:**
> 512MB seems to be the standard size these days...Sounds like a good suggestion to me with respect to "future proof the install". I only have about half of that at 260MB for a triple linux OS boot set up; my EFI partition is currently at about 110 MB (42%) usage and have never had a problem with it filling up. [s]I do regularly purge old kernels after installation of a new kernel and a test run of the new kernel in any of the 3 installed systems. As a result of regular cleaning/kernel purging my EFI partition is adequate, others may need larger though.[/s]

**Edit:** I just realized purging old kernels doesn't affect the size of the EFI partition usage just the boot folder size that the EFI partition is mounted into :redface:. Also I have just reduced my EFI usage to about 78 MB (36 %) by deleting a no longer used folder in /boot/EFI for rEFInd. 256/260 MB would probably suffice if you later on want to dual boot etc. If you only ever want to use a single install probably 128/130 MB would be ample (see TheFu's answer next).

---

### Post by TheFu on 2022-02-11
> **rsteinmetz70112 said:**
> I am replacing and updating the storage in one of my computers. I don't need it now but to preserve my options I intend to create an EFI partition to future proof the install. How big should I make it? I don't have any idea How I might use it in the future. I've seen statements the 100MB will work but 200 would be better and also recommendations for 550 MB.

What future are you trying to "proof" against?

My only EFI systems here:
```

host01 | CHANGED | rc=0 >>
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda1      vfat  511M  4.5M  507M   1% /boot/efi

host02 | CHANGED | rc=0 >>
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/vda1      vfat  511M  7.1M  504M   2% /boot/efi

```
So, it uses less than 10MB.  Say I need 3 copies and round up to 50MB.  That would be fine.  I remember when I had a 20MB HDD (5.25inch RLL), so I'm a little unwilling to just blow space for no good reason.

One machine has LUKS encryption with LVM and was installed with 16.04 initially. It runs 18.04 now. It will never dual boot.  Whenever we look through these forums for storage layouts, people seem to all use less than 100MB for EFI.  I can see reasons to make /boot/ 500MB-1GB ... 
A quick ansible run shows ...
```
$ ansible -i hosts -a "df -Th /boot" cur

host01 | CHANGED | rc=0 >>
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdb1      ext2  720M  168M  516M  25% /boot

host02 | CHANGED | rc=0 >>
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/vda1      ext2  720M  140M  544M  21% /boot

host03 | CHANGED | rc=0 >>
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/vda1      ext2  472M  171M  278M  39% /boot

host04 | CHANGED | rc=0 >>
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda2      ext2  721M  260M  425M  38% /boot

host05 | CHANGED | rc=0 >>
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda2      ext2  237M  195M   30M  87% /boot

```
One system did go above 550MB during a system LTS --> LTS upgrade.  I went back and manually removed the prior kernels.  Same after HWE kernel installs. A few weeks after the HWE, I manually remove the old kernel line. 500 MB was just a little tight, so I changed to 750MB for /boot/. I don't really remember, perhaps there were 3 different kernel lines on that box concurrently.

Anyway, hope these facts are helpful, though likely very incomplete for your needs.

---

### Post by oldfred on 2022-02-11
I like larger ESP if drive is larger. I use small ESP on my smaller flash drives with full installs.

I update UEFI, but my UEFI reads the update file from a FAT32 partition. I could add another or use flash drive, but I normally just use ESP since it is there and large enough.

Some systems now use SystemD boot and if a user may want to experiment with it instead of grub, you will need a larger ESP as more of the boot files maybe in the ESP.

Otherwise smaller ESP works. Many dual boot Windows & Ubuntu with Windows old default of 100MB.

---

### Post by rsteinmetz70112 on 2022-02-12
> **TheFu said:**
> What future are you trying to "proof" against?

Anyway, hope these facts are helpful, though likely very incomplete for your needs.

If I knew the future I wouldn't need to ask.  :cool:

Thanks everyone.

I don't know what my needs might be, at present I have no use for it but may have in the future. 
It seems that some manufacturers are moving to eliminate the BIOS compatibility option in newer machines/motherboards.
I just want to be ready.

I think I'll go with 512MB, that seems the upper limit of what people find useful.  I've gotten over scrimping on disk space since the days when my first hard drive was 20MB and I had a 386 CAD computer running XENIX with  4MB of Ram and a full height 5 1/4'" 160MB ESDI hard drive.

---

