---
title: "Various Questions and issues"
date: 2007-07-19
forum: General Help
---

### Post by TygerTung on 2007-07-19
Hello everyone!

I just installed Feisty Fawn last night and it seems good apart from a few issues and questions I have!

It seems to take quite a long time to load up, around 4 minutes, is that normal?

I am on the install remove programs list and it seems a lot of the programs are for kde, does that mean I cannot use them on normal ubuntu, do I need to have kubuntu insted?

Also to use an apostrophe ´ I need to push the apostrophe button twice, is that normal?

What program would you recommend for  listening to all my mp3 and wmv collection?

I also just brought a DVD recorder, what is the best program to use to copy some DVDs? I think I need to bypass the copy protection and shrink them so that they will fit on a single layer disc?

I think that is all for now!

Cheers,

Sam:guitar:

---

### Post by yabbadabbadont on 2007-07-19
> **TygerTung said:**
> It seems to take quite a long time to load up, around 4 minutes, is that normal?It depends upon how new/old your hardware is.  Older hardware, or a system with low memory, can take longer to boot.

> **TygerTung said:**
> I am on the install remove programs list and it seems a lot of the programs are for kde, does that mean I cannot use them on normal ubuntu, do I need to have kubuntu insted?No.  You can use KDE programs in Gnome and Gnome programs in KDE.  They just tend to look prettier when run in their native desktop environment.

> **TygerTung said:**
> Also to use an apostrophe ´ I need to push the apostrophe button twice, is that normal?The only thing that I can think of is that perhaps you have the wrong keyboard layout configured.  Are you sure that you chose the correct one when installing?

> **TygerTung said:**
> What program would you recommend for  listening to all my mp3 and wmv collection?With the right codecs/plugins installed, there are several different options.  I tend to use either mpd or audacious to listen to music and either mplayer or xine for watching movies.

> **TygerTung said:**
> I also just brought a DVD recorder, what is the best program to use to copy some DVDs? I think I need to bypass the copy protection and shrink them so that they will fit on a single layer disc?k9copy is probably the first program you will want to try as it is a lot like DVDShrink for Windows.  k3b is usually the program most recommended for doing the actual burning of CDs and DVDs though.

---

### Post by TygerTung on 2007-07-19
My computer is an older one these days, although not a shitter I thought!

It's a P4 Prescott 3.GHz
1024mb Ram
Albatron PX5PE Pro mother board
Samsung 120GB hard drive with XP on it
Seagate 160GB hard drive with Feisty Fawn on it.
And a DVD writer and a Combo drive

Sorted out the keyboard issue it was on the wrong one!

I think I have a few more things cleared up now!

---

### Post by yabbadabbadont on 2007-07-19
That machine shouldn't take that long to boot...  The only time it should take a few minutes to boot would be every once in a while when it performs a filesystem check during startup.

---

### Post by TygerTung on 2007-07-19
I have only loaded it a couple of times.

I had Dapper Drake installed for a very small amount of time and that didn't take nearly as long to load up.

Oh one more question, I installed using the alternative CD as the normal one would just crash out when I tried to load it using that, this doesn't give me any limited functionality does it?:popcorn:

---

### Post by yabbadabbadont on 2007-07-19
No, the alternate CD provides the same system in the end.  The install process is just a little different.  You might want to use sudo to start an editor and edit your /boot/grub/menu.lst file and remove the word "splash" wherever you see it.  Then the next time you boot, you might be able to see where the boot process is hanging up before it continues.

---

### Post by TygerTung on 2007-07-19
Where can I find this 'sudo' you speak of?

I'm pretty new to linux

---

### Post by yabbadabbadont on 2007-07-19
In a terminal window, run:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst
```
Find a line that looks like this:
```
# defoptions=quiet splash
```
Remove the word "splash" but don't change anything else.  Save your changes and exit.  Now run:
```
sudo update-grub
```
Finally, reboot and see if you can tell at which point the boot is stalling out.

---

### Post by TygerTung on 2007-07-19
Hi,

Did that and various error messages came up. Seems linux doesn't like my ata, whatever that is.

Took a photo so you could see![ATTACH]38651[/ATTACH]

What do you reckon?

---

### Post by yabbadabbadont on 2007-07-20
It appears to be complaining about the second serial ata channel.  (SATA)  I don't know why it would do that, but at least now you have some information with which to start your search.  ;)

---

### Post by TygerTung on 2007-07-20
I am not using any sata devices though, I didn't actually know I had sata!!!!

I am not really a computer expert, any idea how I could fix this issue?

Maybe the sata ports are not responding because I don't have any sata devices?

All my hard drives and optical drives are IDE!!!!!

---

### Post by yabbadabbadont on 2007-07-20
Hmmm, perhaps I misinterpreted the output.  When booted, run in a terminal window: ```
dmesg | grep -i ata
``` and please post the output.

---

### Post by TygerTung on 2007-07-20
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[   18.283558] Memory: 1028308k/1048512k available (1992k kernel code, 19508k reserved, 900k data, 328k init, 131008k highmem)
[   18.283575]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[    2.684384] libata version 2.20 loaded.
[    2.686025] ata_piix 0000:00:1f.1: version 2.10ac1
[    2.686130] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[    2.686170] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[    2.686191] scsi0 : ata_piix
[    2.897660] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[    2.897665] ata1.00: ATA-7: ST3160812A, 3.AAJ, max UDMA/100
[    2.897668] ata1.00: 312581808 sectors, multi 16: LBA48 
[    2.897775] ata1.01: ata_hpa_resize 1: sectors = 234493056, hpa_sectors = 234493056
[    2.897778] ata1.01: ATA-7: SAMSUNG SP1203N, TL100-30, max UDMA/100
[    2.897780] ata1.01: 234493056 sectors, multi 16: LBA48 
[    2.955874] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[    2.955878] ata1.00: configured for UDMA/100
[    2.963612] ata1.01: ata_hpa_resize 1: sectors = 234493056, hpa_sectors = 234493056
[    2.963615] ata1.01: configured for UDMA/100
[    2.963626] scsi1 : ata_piix
[    3.446750] ata2.00: ATAPI, max UDMA/66
[    3.446753] ata2.01: ATAPI, max UDMA/33
[    3.446758] ata2.00: limited to UDMA/33 due to 40-wire cable
[    3.610486] ata2.00: configured for UDMA/33
[    3.774226] ata2.01: configured for UDMA/33
[    3.774359] scsi 0:0:0:0: Direct-Access     ATA      ST3160812A       3.AA PQ: 0 ANSI: 5
[    3.774520] scsi 0:0:1:0: Direct-Access     ATA      SAMSUNG SP1203N  TL10 PQ: 0 ANSI: 5
[    9.265403] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[    9.265450] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 data 36 in
[   16.254400] ata2: port is slow to respond, please be patient (Status 0xd0)
[   39.234091] ata2: port failed to respond (30 secs, Status 0xd0)
[   39.234134] ata2: soft resetting port
[   39.881256] ata2.00: configured for UDMA/33
[   40.044996] ata2.01: configured for UDMA/33
[   40.045010] ata2: EH complete
[   45.536176] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   45.536221] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 data 36 in
[   52.525158] ata2: port is slow to respond, please be patient (Status 0xd0)
[   75.504867] ata2: port failed to respond (30 secs, Status 0xd0)
[   75.504909] ata2: soft resetting port
[   76.152027] ata2.00: configured for UDMA/33
[   76.315765] ata2.01: configured for UDMA/33
[   76.315779] ata2: EH complete
[   81.806943] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   81.806989] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 data 36 in
[   88.799920] ata2: port is slow to respond, please be patient (Status 0xd0)
[  111.779629] ata2: port failed to respond (30 secs, Status 0xd0)
[  111.779672] ata2: soft resetting port
[  112.426787] ata2.00: configured for UDMA/33
[  112.590528] ata2.01: configured for UDMA/33
[  112.590542] ata2: EH complete
[  118.081707] ata2.00: limiting speed to UDMA/25:PIO4
[  118.081712] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  118.081757] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 data 36 in
[  125.074682] ata2: port is slow to respond, please be patient (Status 0xd0)
[  148.054392] ata2: port failed to respond (30 secs, Status 0xd0)
[  148.054434] ata2: soft resetting port
[  148.701594] ata2.00: configured for UDMA/25
[  148.865292] ata2.01: configured for UDMA/33
[  148.865315] ata2: EH complete
[  149.312077] EXT3-fs: mounted filesystem with ordered data mode.

It spat out this, any use?

---

### Post by TygerTung on 2007-07-20
I can't seem to work out what the ata2 is, I know what ata0 and ata1 is, they're my ide channels, but what ata2 is, I don't know.

I disabled serial ata in the bios to see if that made a difference, but it did nothing!

---

### Post by yabbadabbadont on 2007-07-22
Do you have anything connected to the secondary IDE connector?  A drive (hard, CD, DVD) that is using an older 40 wire IDE cable?

```
[ 3.446758] ata2.00: limited to UDMA/33 due to 40-wire cable
```

If you do, and it is the only thing connected to that cable, make sure that it has been jumpered as Master and not Slave or Cable Select.

---

### Post by TygerTung on 2007-07-23
Yeah I worked out that it was one of the cd rom drives, when I disconnected it it seemed to work sweet as.

---

