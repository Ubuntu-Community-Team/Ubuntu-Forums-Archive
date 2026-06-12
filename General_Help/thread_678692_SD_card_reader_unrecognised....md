---
title: "SD card reader unrecognised..."
date: 2008-01-26
forum: General Help
---

### Post by El_Belgicano on 2008-01-26
I've been searching the forums for a while now but I still can't read/write and even mount or find the mount point of my built in SD card reader. (see sig for the specs)
In some threads I found that the outputs of various commands could be useful to resolve the problem:

1) **dmesg | tail** :
```
[ 8083.320000] pccard: PCMCIA card inserted into slot 0
[ 8083.320000] pcmcia: registering new device pcmcia0.0
```
Note: I assume the system "feels" the new device ...

2) **sudo fdisk -l** :
```
Disque /dev/sda: 60.0 Go, 60011642880 octets
255 heads, 63 sectors/track, 7296 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc2d3c2d3

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1               1         230     1847443+  1b  Hidden W95 FAT32
/dev/sda2   *         231        4474    34089930    c  W95 FAT32 (LBA)
/dev/sda3            4475        6085    12940357+   f  W95 Etendu (LBA)
/dev/sda4            6086        7296     9727357+  83  Linux
/dev/sda5            4475        5107     5084541    b  W95 FAT32
/dev/sda6            5108        5204      779121   82  Linux swap / Solaris
/dev/sda7            5205        6085     7076601   83  Linux

Disque /dev/sdb: 160.0 Go, 160041885696 octets
255 heads, 63 sectors/track, 19457 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6455d99f

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS
```
Note: no traces of SDcards here...

3) **lspci | grep Ricoh** :
```
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:01.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:01.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
```

So, I hope someone can interpret the outputs and give me some advice on how to get the reader working.
Thanks in advance.

EDIT: also reading a lot of people with built in card readers able to work with SD-card but not Memory Stick or others, but I can't even get the SD to be seen by the system.

---

### Post by ayoli on 2008-01-26
here's my dmesg output when I insert my SD card in my builtin sd/mmc card reader :
```
[ 6103.320516] tifm_core: MMC/SD card detected in socket 0:1
[ 6103.765147] mmcblk0: mmc1:e624 SD01G 992000KiB 
[ 6103.765183]  mmcblk0: p1
```
I just work out of the box (it wasn't with feisty), btw, I haven't the same as you. See my lspci output:
```
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
02:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```
You may want to have a look to [this thread]("http://ubuntuforums.org/showthread.php?t=644779"), it could help you.

---

### Post by El_Belgicano on 2008-01-26
Thanks for the thread but it didn't change anything, still no mounting ...

---

### Post by ayoli on 2008-01-26
After inserting your sd card, what is the output of (in a terminal) :
```
dmesg |grep -i mmc
```
also what is the outpout of :
```
lsmod |grep -i tifm
```

---

### Post by El_Belgicano on 2008-01-26
```
dmesg |grep -i mmc
[    4.696000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
```
&
```
lsmod |grep -i tifm
tifm_sd                12808  0 
mmc_core               28420  1 tifm_sd
tifm_core              11268  1 tifm_sd
```

---

### Post by ayoli on 2008-01-26
well, you dmesg out put, tells it didn't see your inserted  card, but it can see the reader and the system have loaded the modules.
if I find a way to fix that I'll post it here. unfortunately, no idea atm.

---

### Post by El_Belgicano on 2008-02-01
Bump...

---

### Post by jabapyth on 2008-02-01
Try going to System settings, then "Hard disks and filesystems" in the advanced tab. If you see your reader there, you can create a mount point for it, and enable it.

---

### Post by El_Belgicano on 2008-03-16
bump again, ...

---

