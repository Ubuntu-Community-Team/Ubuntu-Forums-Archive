---
title: "Cant mount or fdisk or mkfs.ext3 on micro sdcard kingston 16gb"
date: 2013-02-11
forum: General Help
---

### Post by t3ch on 2013-02-11
Hello all, i have problems with mounting or running fdisk or formating micro sdcard. When i put in to 

lspci -> 16:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20)

it show /dev/mmcblk0

but when i run fdisk /dev/mmcblk0 i get:
# fdisk /dev/mmcblk0
fdisk: unable to read /dev/mmcblk0: Input/output error

similar thing with mkfs.ext3

And it work on win7 :/

What to do? 

tnx

EDIT 1: 
( and dmesg shows this )
[  919.625759] mmc0: Controller never released inhibit bit(s).
[  919.631933] mmcblk0: error -5 sending status command, retrying
[  919.632043] mmcblk0: timed out sending SET_BLOCK_COUNT command, card status 0x400900

---

### Post by alephan on 2013-02-13
Have the same issue:

8281.695274] mmcblk0: timed out sending SET_BLOCK_COUNT command, card status 0x400900
[ 8281.695334] mmcblk0: timed out sending SET_BLOCK_COUNT command, card status 0x400900
[ 8281.695337] end_request: I/O error, dev mmcblk0, sector 0
[ 8281.695412] mmcblk0: timed out sending SET_BLOCK_COUNT command, card status 0x400900
[ 8281.695472] mmcblk0: timed out sending SET_BLOCK_COUNT command, card status 0x400900
[ 8281.695531] mmcblk0: timed out sending SET_BLOCK_COUNT command, card status 0x400900
[ 8281.695592] mmcblk0: timed out sending SET_BLOCK_COUNT command, card status 0x400900
[ 8281.695652] mmcblk0: timed out sending SET_BLOCK_COUNT command, card status 0x400900
[ 8281.695713] mmcblk0: timed out sending SET_BLOCK_COUNT command, card status 0x400900
[ 8281.695716] end_request: I/O error, dev mmcblk0, sector 0

---

### Post by t3ch on 2013-02-14
i have buyed canyon usb sdcard reader and now it work.. otherwise no success.. :)

---

