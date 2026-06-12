---
title: "CD-Audio Problem w/ Plextor UltraPlex Wide CD-ROM"
date: 2008-06-16
forum: General Help
---

### Post by Michael_B on 2008-06-16
Hello:

I've recently installed Ubuntu 8.04 on an Intel P4-based system possessing an Adaptec 29160 SCSI adapter. Attached to this adapter are a pair of internal SCSI hard disks, as well as a Plextor UltraPlex Wide SCSI CD-ROM (reported as PX-40TW by dmesg and /proc/scsi/scsi; output below.) Cables and termination are fine.

Also attached to this computer is an external (USB) Plextor PX-810 UF DVD+RW burner.

The UltraPlex seems to work fine for reading *data* CD-ROMs with Ubuntu / Linux (in fact it was from this device that I installed Ubuntu 8.04 from the downloaded .iso.) However, CD-audio, either played directly from, or ripped using this CD-ROM is completely garbled. I have tried making a copy of a CD-ROM (using both k3b and Brasero) and the resultant (copy) CD contains only high-pitched squealing, chirps, and other noise. Interestingly, on the copy (a) there are discrete tracks, and (b) the CD-TEXT information seems to have been read OK.

Additional information:

- If I try to simply *play* (not copy) an audio CD using this drive, I get the same result-- high pitched squeals and chirping sounds. It seems like there is a fundamental problem in reading CD-audio from this drive with this version of Ubuntu / Linux.

- Audio played, ripped, or burned using my other drive, the PX-810UF, works perfectly, so it doesn't seem like a problem with the actual audio playing / extraction software I've tried.

- The UltraPlex Wide drive works fine for all data and audio (playing, extracting / ripping) tasks under Windows XP. So the hardware is not faulty, nor is there a problem with the SCSI chain (termination, etc.)

- This problem also exists with this same machine/setup under Fedora 9 (fresh install from the DVD .iso.) In fact it was this problem that let me to give Ubuntu a try for the first time. I'm quite impressed so far!

- My Ubuntu installation is 8.04 Desktop, with updated packages via apt-get update and apt-get upgrade. Again, this was installed with the UltraPlex Wide, so the problem seems to be audio-only.

I am inclined to think there might be an issue with the kernel, the SCSI driver, or some combination of the two.

I am curious if anyone else has observed behavior similar to this, and any pointers, suggestions, or fixes would be most appreciated! Please let me know what additional system information might be useful and I'll be happy to post it.

Best regards,
-Michael

Linux mdb 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux

[ 67.725335] scsi3 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[ 67.725337] <Adaptec 29160 Ultra160 SCSI adapter>

Host: scsi3 Channel: 00 Id: 06 Lun: 00
Vendor: PLEXTOR Model: CD-ROM PX-40TW Rev: 1.05
Type: CD-ROM ANSI SCSI revision: 02

---

### Post by Mahesh78 on 2008-06-29
I have the same problem with two external Plextor PX-40TS drives connected to my laptop through an Adaptec 1480A PCCard SCSI adapter. Data CD-ROMs work fine, but audio-CDs won't play at all. Gnome complains that the inserted disc is not an Audio CD, see attached file 'Screenshot.png'.

Here's what dmesg outputs after the above Gnome error message:
```

[23561.567379] (scsi8:A:3:0): No or incomplete CDB sent to device.
[23561.567587] scsi8: Issued Channel A Bus Reset. 1 SCBs aborted

```

Here's what dmesg outputs after I insert the SCSI card:
```
 
[21222.216165] pccard: CardBus card inserted into slot 0
[21222.216528] PCI: Enabling device 0000:03:00.0 (0000 -> 0003)
[21222.216544] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[21222.216564] PCI: Setting latency timer of device 0000:03:00.0 to 64
[21222.216653] aic7xxx: PCI Device 3:0:0 failed memory mapped test.  Using PIO.
[21222.217842] ahc_pci:3:0:0: Host Adapter Bios disabled.  Using default SCSI device parameters
[21237.218044] scsi8 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[21237.218048]         <Adaptec 1480A Ultra SCSI adapter>
[21237.218050]         aic7860: Ultra Single Channel A, SCSI Id=7, 3/253 SCBs
[21237.218053] 
[21237.752689] scsi 8:0:2:0: CD-ROM            PLEXTOR  CD-ROM PX-40TS   1.14 PQ: 0 ANSI: 2
[21237.752715]  target8:0:2: Beginning Domain Validation
[21237.757008]  target8:0:2: FAST-20 SCSI 20.0 MB/s ST (50 ns, offset 15)
[21237.759462]  target8:0:2: Domain Validation skipping write tests
[21237.759470]  target8:0:2: Ending Domain Validation
[21237.768145] scsi 8:0:3:0: CD-ROM            PLEXTOR  CD-ROM PX-40TS   1.14 PQ: 0 ANSI: 2
[21237.768165]  target8:0:3: Beginning Domain Validation
[21237.772619]  target8:0:3: FAST-20 SCSI 20.0 MB/s ST (50 ns, offset 15)
[21237.775051]  target8:0:3: Domain Validation skipping write tests
[21237.775059]  target8:0:3: Ending Domain Validation
[21238.576956] sr1: scsi-1 drive
[21238.577061] sr 8:0:2:0: Attached scsi CD-ROM sr1
[21238.577140] sr 8:0:2:0: Attached scsi generic sg2 type 5
[21238.587711] sr2: scsi-1 drive
[21238.587753] sr 8:0:3:0: Attached scsi CD-ROM sr2
[21238.587784] sr 8:0:3:0: Attached scsi generic sg3 type 5

```

The drives work just fine with WinXP, including audio-CDs. Hope someone can help with this problem. I use the drives for ripping my CD-collection to FLAC-files...

---

