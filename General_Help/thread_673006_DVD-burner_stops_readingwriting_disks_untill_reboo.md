---
title: "DVD-burner stops reading/writing disks untill reboot"
date: 2008-01-20
forum: General Help
---

### Post by Kimm on 2008-01-20
This is a strange problem that started happening when I bought my new computer (all new, the Burner is new).

When I start the computer I can read and write discs just fine, but after a while (I cant tell how long exactly) it will just stop. I can be in the middle of the process of transfering files from a disk to the HDD, or watching a DVD, or burning a disk. It will just stop, no warning, nothing.

I'm sure you can see how this is a problem, disks in the process of being burnt will become corrupted, and the same goes for files that are being transfered. And if I'm watching a movie, it will just stop playing.

I googled a bit and found a post about a similar problem, aparently caused by power saving-settings in the OS. However this was in OS X, and I am not able to find any such settings in the control panel of Ubuntu.

Can anyone please explain what is happening? and how I can solve it?

I have checked the system log, and this is where I started burning a disk today:

```

Jan 20 14:54:15 Haze kernel: [ 6190.952192] cdrom: This disc doesn't have any tracks I recognize!
Jan 20 14:57:36 Haze kernel: [ 6391.787511] hdc: DMA interrupt recovery
Jan 20 14:57:36 Haze kernel: [ 6391.787516] hdc: lost interrupt
Jan 20 15:01:19 Haze kernel: [ 6614.710086] hdc: DMA interrupt recovery
Jan 20 15:01:19 Haze kernel: [ 6614.710092] hdc: lost interrupt
Jan 20 15:02:21 Haze kernel: [ 6676.352112] hdc: DMA interrupt recovery
Jan 20 15:02:21 Haze kernel: [ 6676.352116] hdc: lost interrupt
Jan 20 15:06:58 Haze kernel: [ 6953.693713] UDF-fs: No VRS found
Jan 20 15:07:17 Haze kernel: [ 6972.058261] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Jan 20 15:07:17 Haze kernel: [ 6972.058267] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
Jan 20 15:07:17 Haze kernel: [ 6972.058270] ide: failed opcode was: unknown
Jan 20 15:07:17 Haze kernel: [ 6972.058513] end_request: I/O error, dev hdc, sector 696664
Jan 20 15:07:37 Haze kernel: [ 6992.833882] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
Jan 20 15:07:37 Haze kernel: [ 6992.833888] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
Jan 20 15:07:37 Haze kernel: [ 6992.833890] ide: failed opcode was: unknown
Jan 20 15:07:46 Haze kernel: [ 7001.725237] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
Jan 20 15:07:46 Haze kernel: [ 7001.725243] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
Jan 20 15:07:46 Haze kernel: [ 7001.725245] ide: failed opcode was: unknown
Jan 20 15:07:55 Haze kernel: [ 7010.541717] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
Jan 20 15:07:55 Haze kernel: [ 7010.541723] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
Jan 20 15:07:55 Haze kernel: [ 7010.541726] ide: failed opcode was: unknown
Jan 20 15:08:04 Haze kernel: [ 7019.484881] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
Jan 20 15:08:04 Haze kernel: [ 7019.484888] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
Jan 20 15:08:04 Haze kernel: [ 7019.484890] ide: failed opcode was: unknown
Jan 20 15:08:04 Haze kernel: [ 7019.484893] hdc: DMA disabled
Jan 20 15:08:04 Haze kernel: [ 7019.535109] hdc: ATAPI reset complete
Jan 20 15:08:13 Haze kernel: [ 7028.379516] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
Jan 20 15:08:13 Haze kernel: [ 7028.379522] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
Jan 20 15:08:13 Haze kernel: [ 7028.379524] ide: failed opcode was: unknown
Jan 20 15:08:22 Haze kernel: [ 7037.249022] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
Jan 20 15:08:22 Haze kernel: [ 7037.249028] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
Jan 20 15:08:22 Haze kernel: [ 7037.249030] ide: failed opcode was: unknown
Jan 20 15:08:31 Haze kernel: [ 7046.143778] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
Jan 20 15:08:31 Haze kernel: [ 7046.143785] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
Jan 20 15:08:31 Haze kernel: [ 7046.143787] ide: failed opcode was: unknown
Jan 20 15:08:31 Haze kernel: [ 7046.192600] hdc: ATAPI reset complete
Jan 20 15:08:31 Haze kernel: [ 7046.193066] end_request: I/O error, dev hdc, sector 696700
Jan 20 15:08:33 Haze kernel: [ 7048.161891] VFS: busy inodes on changed media.

```

---

### Post by Rotaj on 2008-01-20
My first instinct says this might be a heat issue. Can you reboot immediately or do you have to wait? 

When you remove a disc from this optical drive, does it feel excessively warm?

---

### Post by Kimm on 2008-01-20
> **Rotaj said:**
> My first instinct says this might be a heat issue. Can you reboot immediately or do you have to wait?

I can reboot diretly

> **Rotaj said:**
> 
When you remove a disc from this optical drive, does it feel excessively warm?

Not really. It feels about as warm as they usually do. And shouldn't the drive start working again after it has cooled off? I have to reboot if I want it working again :/

---

### Post by Rotaj on 2008-01-20
OK, not a heat issue. Was your computer prebuilt or did you assemble it yourself?

Prebuilt = Contact customer support

Home built = Ensure good connections for all drives, Jumpers are correct. if that fails, RMA the optical drive

---

### Post by Kimm on 2008-01-20
> **Rotaj said:**
> OK, not a heat issue. Was your computer prebuilt or did you assemble it yourself?

Prebuilt = Contact customer support

Home built = Ensure good connections for all drives, Jumpers are correct. if that fails, RMA the optical drive

It is home built.
I will do that. I was hoping it was a software issue though :/ I will also try to connect an old drive that I know works.

---

