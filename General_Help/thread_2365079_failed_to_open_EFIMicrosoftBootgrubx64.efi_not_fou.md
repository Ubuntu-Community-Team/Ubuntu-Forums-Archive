---
title: "failed to open /EFI/Microsoft/Boot/grubx64.efi not found"
date: 2017-07-02
forum: General Help
---

### Post by xoogler on 2017-07-02
[SIZE=5][SIZE=1]good morning, so I had linuxmint-18-cinnamon-64bit on one  of my partitions and tried to make a dual boot I had several problems I  couldn't have the dual boot because when booting it displayed grub  without a windows 7 entry anyway I used a windows 7 cd and fixed the mbr  so system boots to windows 7 only but i had linux on the other  partition i kept working with windows 7 when i booted to windows 7 i  deleted Linux Partition and merged it with windows partition using EAseus  now after reboot as asked by easeus, easeus was first program to load  in windows and merged the partitions but after automatic rebooting i get  the errors shown in a black screen
 ```
failed to open /EFI/Microsoft/Boot/grubx64.efi not found 
failed to load image /EFI/Microsoft/Boot/grubx64.efi not found
start_image returned not found
``` 
I tried booting to windows via BIOS but same error
here are some of the commands i used and their results via a LIVE USB
```
mint@mint ~ $ sudo efibootmgr -v
BootCurrent: 000E
Timeout: 0 seconds
BootOrder: 000A,0003,000B,000E,000C,000D
Boot0003* UEFI: IP4 Realtek PCIe GBE Family Controller    PciRoot(0x0)/Pci(0x1c,0x3)/Pci(0x0,0x2)/MAC(ac220bd730d8,0)/IPv4(0.0.0.0:0<->0.0.0.0:0,0,0)AMBO
Boot000A* Windows Boot Manager    HD(1,MBR,0x113,0x800,0xaf000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)
Boot000B* ubuntu    HD(1,MBR,0x113,0x800,0xaf000)/File(EFI\Ubuntu\grubx64.efi)
Boot000C* Hard Drive     BBS(HD,,0x0)AMGOAMNO........o.S.T.5.0.0.L.T.0.1.2.-.1.D.G.1.4.2....................A...........................>..Gd-.;.A..MQ..L. . . . . . . . . . . . .3.W.B.P.T.C.F.D......AMBOAMNO........y.T.O.S.H.I.B.A. .T.r.a.n.s.M.e.m.o.r.y. .1...0.0....................A.............................F..Gd-.;.A..MQ..L.T.O.S.H.I.B.A. .T.r.a.n.s.M.e.m.o.r.y. .1...0.0......AMBO
Boot000D* CD/DVD Drive     BBS(CDROM,,0x0)AMGOAMNO........o.T.S.S.T.c.o.r.p. .C.D.D.V.D.W. .S.U.-.2.2.8.C.B....................A...........................>..Gd-.;.A..MQ..L.9.R.Q.3.Y.6.D.C.0.6.F.2.6.X. . . . . . ......AMBO
Boot000E* UEFI: TOSHIBA TransMemory 1.00    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(1,0)/HD(1,MBR,0x46,0x15470,0x1280)AMBO
```

as for the tree on /dev/sda1
```
int@mint /media/abcd $ tree
.
&#9500;&#9472;&#9472; Boot
&#9474;   &#9500;&#9472;&#9472; BCD
&#9474;   &#9500;&#9472;&#9472; BCD.LOG
&#9474;   &#9500;&#9472;&#9472; BCD.LOG1
&#9474;   &#9500;&#9472;&#9472; BCD.LOG2
&#9474;   &#9500;&#9472;&#9472; BOOTSTAT.DAT
&#9474;   &#9500;&#9472;&#9472; cs-CZ
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; da-DK
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; de-DE
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; el-GR
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; en-US
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; es-ES
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; fi-FI
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; Fonts
&#9474;   &#9474;   &#9500;&#9472;&#9472; chs_boot.ttf
&#9474;   &#9474;   &#9500;&#9472;&#9472; cht_boot.ttf
&#9474;   &#9474;   &#9500;&#9472;&#9472; jpn_boot.ttf
&#9474;   &#9474;   &#9500;&#9472;&#9472; kor_boot.ttf
&#9474;   &#9474;   &#9492;&#9472;&#9472; wgl4_boot.ttf
&#9474;   &#9500;&#9472;&#9472; fr-FR
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; hu-HU
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; it-IT
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; ja-JP
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; ko-KR
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; memtest.exe
&#9474;   &#9500;&#9472;&#9472; nb-NO
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; nl-NL
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; pl-PL
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; pt-BR
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; pt-PT
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; ru-RU
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; sv-SE
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; tr-TR
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; zh-CN
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; zh-HK
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9492;&#9472;&#9472; zh-TW
&#9474;       &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9500;&#9472;&#9472; bootmgr
&#9500;&#9472;&#9472; boot-sav
&#9474;   &#9500;&#9472;&#9472; sda2
&#9474;   &#9500;&#9472;&#9472; sda5
&#9474;   &#9492;&#9472;&#9472; sdb2
&#9492;&#9472;&#9472; EFI
    &#9500;&#9472;&#9472; Boot
    &#9474;   &#9500;&#9472;&#9472; bootx64.efi
    &#9474;   &#9492;&#9472;&#9472; bootx64.efi.grb
    &#9492;&#9472;&#9472; Microsoft
        &#9492;&#9472;&#9472; Boot
            &#9500;&#9472;&#9472; bootmgfw.efi
            &#9500;&#9472;&#9472; bootmgfw.efi.grb
            &#9500;&#9472;&#9472; bootx64.efi
            &#9492;&#9472;&#9472; bootx64.efi.grb

33 directories, 43 files
```

Secure boot is disabled and for /dev/sda2 it is set as boot but even when locating /dev/sda1 as boot error persists

```
mint@mint /media/abcd $ sudo fdisk -l

Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x01091c71

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1            2048    718847    716800   350M ef EFI (FAT-12/16/32)
/dev/sda2  *       718848 314568764 313849917 149.7G  7 HPFS/NTFS/exFAT
/dev/sda3       314576894 976773119 662196226 315.8G  f W95 Ext'd (LBA)
/dev/sda5       314576896 955801599 641224704 305.8G  7 HPFS/NTFS/exFAT
/dev/sda6       955803648 976773119  20969472    10G 82 Linux swap / Solaris

Partition 3 does not start on physical sector boundary.


```

I tried with boot-repair but didn't fix the error[/SIZE]
[/SIZE]

---

### Post by johndough2 on 2017-07-02
Hi

The first thing would be to put it back as a W7 only boot and install.  Even if it means a fresh install.

Delete any partitions not currently used by W7, leaving a lot of free space.

When that is sorted and stable, if you want linux on again I would suggest 5 new partitions.
1 A good sized Storage area NTFS, so it is common to both OS's
2 small BOOT area, for Grub
3 Medium ROOT /
4 Largish /home
5 small but significant SWAP

One thing I found with triple booting was to name the partitions that would be generating a boot loader.
EG:  OpenSuse, Windows and Zedebian then the BIOS on this lappy goes to Opensuse.  If it just Debian then the Debian bootloader was called first.

Ah! The Magic Roundabout...[https://www.youtube.com/watch?v=2zCGjSoZzkY](https://www.youtube.com/watch?v=2zCGjSoZzkY) and if that don't explain the madness of trying to get a computer to just work, then I don't know what would.

---

### Post by oldfred on 2017-07-02
Please use standard fonts when posting, otherwise seen as shouting. Just use other fonts or colors to perhaps highlight something critical.

It looks like you must have newer UEFI hard ware, but have/had Windows 7 installed in the now 35 year old BIOS/MBR configuration. Windows 7 default install from DVD is BIOS and in BIOS mode all versions of Windows must use MBR partitioning. Windows 7 installer can be converted to UEFI, but will not work with UEFI if Secure Boot is turned on.

But you have a FAT32 partition on MBR drive which then is seen as an ESP - efi system partition. 
Using UEFI on a MBR partitioned drive is unusual for a full install. The installer is often configured that way only for compatibility to allow BIOS or UEFI install from one flash drive.

Since hardware is UEFI and installs BIOS, did you switch boot modes in UEFI/BIOS? That then can prevent booting. Make sure UEFI is set to boot BIOS mode, which may be CSM or Legacy.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

