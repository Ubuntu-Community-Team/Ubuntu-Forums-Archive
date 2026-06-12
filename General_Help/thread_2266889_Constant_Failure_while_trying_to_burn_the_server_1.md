---
title: "Constant Failure while trying to burn the server 14.04 ISO"
date: 2015-02-26
forum: General Help
---

### Post by mandarpowale on 2015-02-26
Here is the Nero Log. I have tried IMGBURN and Brasero too. Around 3 CD and  3DVD's were wasted, Please help.

```
=====================================================
2X24-K0C1-4899-TXL9-MAX7-8PC2-1H3P-MPW2-X0C3-6ZT5-KAMA-K5CW-0E2P-1EEP-CK7P-049L-97E8-345H-9189-0E7A-HH6P-ECC7-0CC9-CA3H-454T-5KM1-1LA4-8L8Z-5C4W-****-****


Windows XP 5.1
IA32
WinAspi: -


NT-SPTI used
Nero Version: 10.0.23.100
Internal Version: 10,0,23,100
 (Nero Express)
Recorder:             <ASUS DRW-24B5ST>         Version: 1.00 - HA 1 TA 0 - 10.0.23.100
 Adapter driver:      <Serial ATA>              HA 1
 Drive buffer  :      1536kB
 Bus Type      :      via Inquiry data
 Connected to MMC as unknown drive with class-nr : 1
 Drive is autodetected - recorder class: Std. MMC recorder
CD-ROM:               <DTSOFT   BDROM           >Version: 1.05 - HA 1 TA 1 - 10.0.23.100
 Adapter driver:      <IDE>                     HA 1


=== Scsi-Device-Map ===
DiskPeripheral       : WDC WD10PURX-64D85Y0             atapi Port 1 ID 0  DMA: On 
CdRomPeripheral      : ASUS DRW-24B5ST                  atapi Port 2 ID 0  DMA: On 
DiskPeripheral       : WDC WD5000AADS-56S9B0            atapi Port 3 ID 0  DMA: On 


=== CDRom-Device-Map ===
ASUS DRW-24B5ST            I:   CdRom0
DTSOFT BDROM               J:   CdRom1
=======================


AutoRun : 1
Excluded drive IDs: 
WriteBufferSize: 83886080 (0) Byte
BUFE           : 0
Physical memory     : 2047MB (2097151kB)
Free physical memory: 2047MB (2097151kB)
Memory in use       : 14 %
Uncached PFiles: 0x0
Global Bus Type: default (0)
Check supported media : Disabled (0) 


26.2.2015
CD Image
10:59:50 AM    #1 Text 0 File SCSIPTICommands.cpp, Line 464
    LockMCN - completed sucessfully for IOCTL_STORAGE_MCN_CONTROL
    
10:59:50 AM    #2 Text 0 File Burncd.cpp, Line 3166
    ASUS DRW-24B5ST
    FlextraLink activated
    
10:59:50 AM    #3 Text 0 File Burncd.cpp, Line 3496
    Turn on Disc-At-Once, using CD-R/RW media
    
10:59:50 AM    #4 Text 0 File DlgWaitCD.cpp, Line 314
    [I: DRW-24B5ST      ] Last possible write address on media:   359846
    Last address to be written:             304639
    
10:59:50 AM    #5 Text 0 File DlgWaitCD.cpp, Line 326
    [I: DRW-24B5ST      ] Write in overburning mode: NO (enabled: CD)
    
10:59:50 AM    #6 Text 0 File DlgWaitCD.cpp, Line 2890
    Recorder: ASUS DRW-24B5ST;
       CDR code: 00 97 24 16; OSJ entry from: SONY Corporation
       ATIP Data:
         Special    Info [hex] 1: D0 00 A0, 2: 61 18 10 (LI 97:24.16), 3: 4F 3B 4A (LO 79:59.74)
         Additional Info [hex] 1: 00 00 80 (invalid), 2: 00 80 00 (invalid), 3: 00 80 80 (invalid)
    
10:59:50 AM    #7 Text 0 File DlgWaitCD.cpp, Line 499
    [I: DRW-24B5ST      ] >>> Protocol of DlgWaitCD activities: <<<
    =========================================
    
10:59:50 AM    #8 Text 0 File ThreadedTransferInterface.cpp, Line 785
    Setup items (after recorder preparation)
     0: TRM_DATA_MODE1 (2 - CD-ROM Mode 1, Joliet)
        2 indices, index0 (150) not provided
        original disc pos #0 + 304640 (304640) = #304640/67:41.65
        not relocatable, disc pos for caching/writing not required/not required
        -> TRM_DATA_MODE1, 2048, config 0, wanted index0 0 blocks, length 304640 blocks [I: ASUS DRW-24B5ST]
    --------------------------------------------------------------
    
10:59:51 AM    #9 Text 0 File ThreadedTransferInterface.cpp, Line 1001
    Prepare [I: ASUS DRW-24B5ST] for write in CUE-sheet-DAO
    DAO infos:
    ==========
     MCN: ""
     TOCType: 0x00; Session Closed, disc fixated
     Tracks 1 to 1:                                  Idx 0         Idx 1      Next Trk
       1: TRM_DATA_MODE1, 2048/0x00, FilePos             0        307200     624209920, ISRC ""
    DAO layout:
    ===========
     ___Start_|____Track_|_Idx_|_CtrlAdr_|_____Size_|______NWA_|_RecDep__________
         -150 |  lead-in |   0 |    0x41 |        0 |        0 | 0x00
         -150 |        1 |   0 |    0x41 |        0 |        0 | 0x00
            0 |        1 |   1 |    0x41 |   304640 |   304640 | 0x00
       304640 | lead-out |   1 |    0x41 |        0 |        0 | 0x00
    MediaType: CD-R
    
10:59:51 AM    #10 Text 0 File SCSIPTICommands.cpp, Line 251
    SPTILockVolume - completed successfully for FSCTL_LOCK_VOLUME
    
10:59:51 AM    #11 Text 0 File Burncd.cpp, Line 4206
    Caching options: cache CDRom or Network-Yes, small files-Yes (<64KB)
    
10:59:51 AM    #12 PHASE 24 File dlgbrnst.cpp, Line 1827
    Caching of files started
    
10:59:51 AM    #13 Text 0 File Burncd.cpp, Line 4328
    Cache writing successful.
    
10:59:51 AM    #14 PHASE 25 File dlgbrnst.cpp, Line 1827
    Caching of files completed
    
10:59:51 AM    #15 PHASE 36 File dlgbrnst.cpp, Line 1827
    Burn process started at 48x (7,200 KB/s)
    
10:59:51 AM    #16 Text 0 File ThreadedTransferInterface.cpp, Line 2769
    Verifying disc position of item 0 (not relocatable, no disc pos, no patch infos, orig at #0): write at #0
    
10:59:51 AM    #17 Text 0 File MMC.cpp, Line 17596
    StartDAO : CD-Text - Off
    
10:59:51 AM    #18 Text 0 File MMC.cpp, Line 21592
    Set BUFE: FlextraLink -> ON , SMART-BURN : ON
    
10:59:51 AM    #19 Text 0 File MMC.cpp, Line 17824
    CueData, Len=32
    41 00 00 14 00 00 00 00 
    41 01 00 10 00 00 00 00 
    41 01 01 10 00 00 02 00 
    41 aa 01 14 00 43 2b 41 
    
10:59:51 AM    #20 Text 0 File ThreadedTransfer.cpp, Line 273
    Pipe memory size 83836800
    
10:59:59 AM    #21 Text 0 File Cdrdrv.cpp, Line 1275
    10:59:59.578 - I: ASUS DRW-24B5ST : Queue again later
    
11:00:01 AM    #22 SPTI -1500 File SCSIPassThrough.cpp, Line 217
    CdRom0: SCSIStatus(x02) WinError(0) NeroError(-1500)
    CDB Data:   0x2A 00 00 00 00 00 00 00 20 00 00 00 
    Sense Key:  0x04 (KEY_HARDWARE_ERROR)
    Sense Code: 0x08
    Sense Qual: 0x01
    Sense Area: 0x70 00 04 00 00 00 00 0A 00 00 00 00 08 01 
    Buffer x078a0040: Len x10000
    0x45 52 08 00 00 00 90 90 00 00 00 00 00 00 00 00 
    0x00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
    0x33 ED FA 8E D5 BC 00 7C FB FC 66 31 DB 66 31 C9 
    
11:00:01 AM    #23 TRANSFER -20 File ThreadedTransfer.cpp, Line 1222
    Could not perform Write
    
11:00:01 AM    #24 CDR -1500 File Writer.cpp, Line 327
    DMA-driver error. Timeout occurred
    I: ASUS DRW-24B5ST
    
11:00:07 AM    #25 SPTI -1169 File SCSIPassThrough.cpp, Line 217
    CdRom0: SCSIStatus(x02) WinError(0) NeroError(-1169)
    CDB Data:   0x51 00 00 00 00 00 00 00 20 00 00 00 
    Sense Key:  0x02 (KEY_NOT_READY)
    Sense Code: 0x04
    Sense Qual: 0x08
    Sense Area: 0x70 00 02 00 00 00 00 0A 00 00 00 00 04 08 
    Buffer x05779980: Len x20
    
11:00:17 AM    #26 Text 0 File DVDPlusDualLayer.cpp, Line 1460
    SetDriveCaps: Set LAST LBA of layer 1 to 0
    
11:00:17 AM    #27 PHASE 38 File dlgbrnst.cpp, Line 1827
    Burn process failed at 48x (7,200 KB/s)
    
11:00:17 AM    #28 Text 0 File SCSIPTICommands.cpp, Line 301
    SPTIDismountVolume - completed successfully for FSCTL_DISMOUNT_VOLUME
    
11:00:17 AM    #29 Text 0 File Cdrdrv.cpp, Line 11916
    DriveLocker: UnLockVolume completed
    
11:00:17 AM    #30 Text 0 File SCSIPTICommands.cpp, Line 464
    UnLockMCN - completed sucessfully for IOCTL_STORAGE_MCN_CONTROL
    


Existing drivers:


Registry Keys:
HKLM\Software\Microsoft\Windows NT\CurrentVersion\WinLogon\AllocateCDROMs : 1 (Security Option) 
====================================================================================
```

Here is a Brasero Log while I tried to burn the Image using it.
```
==============================================
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1739)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_0GBBUX.bin toc = none
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_95BBUX.bin toc = none
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroChecksumImage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_7ZBBUX.bin toc = none
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /media/mandar/Software/ubuntu-14.04.2-server-amd64.iso (size = 623902720)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 83aabd8dcf1e8f469f3c72fff2375195 ((null) before)
BraseroChecksumImage Finished track successfully
BraseroChecksumImage stopping
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_action
BraseroLibburn unsupported operation
BraseroLibburn deactivating
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_device
BraseroLibburn Drive (/dev/sr0) init result = 1
BraseroLibburn called brasero_job_get_flags
BraseroLibburn called brasero_job_get_media
BraseroLibburn called brasero_job_get_fd_in
BraseroLibburn called brasero_job_get_tracks
BraseroLibburn Setting multi 0
BraseroLibburn Setting burnproof 1
BraseroLibburn Setting dummy 0
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_convert_fs_adr( /dev/sr0 )
BraseroLibburn Writing
BraseroLibburn called brasero_job_set_dangerous
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_is_enumerable_adr( /dev/sr0 ) is true
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Async START UNIT succeeded after 0.1 seconds
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn mmc_set_streaming: end_lba=2297887 ,  r=22160000 ,  w=22160
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Allocating buffer via mmap()
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn dvd/bd Profile= 11h , obs= 32768 , obs_pad= 1
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn DVD pre-track 01 : get_nwa(0), ret= 1 , d->nwa= 0
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI error condition on command 2Ah WRITE(10): [5 21 00] Illegal request. Lba out of range.
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Libburn reported an error SCSI error on write(16,16): [5 21 00] Illegal request. Lba out of range.
BraseroLibburn called brasero_job_error
BraseroLibburn finished with an error
BraseroLibburn asked to stop because of an error
    error        = 1
    message    = "SCSI error on write(16,16): [5 21 00] Illegal request. Lba out of range."
BraseroLibburn stopping
Session error : SCSI error on write(16,16): [5 21 00] Illegal request. Lba out of range. (brasero_burn_record brasero-burn.c:2856)
```

---

### Post by scdbackup on 2015-02-26
Hi,  the decisive error is  >  Sense Key: 0x04 (KEY_HARDWARE_ERROR) Sense Code: 0x08 Sense Qual: 0x01   According to MMC specs this means "Logical unit communication timeout"  [br]x[/br] [br]x[/br] The next error is  >  > Sense Key: 0x02 (KEY_NOT_READY) > Sense Code: 0x04 > Sense Qual: 0x08   "Logical unit not ready, long write in progress" [br]x[/br]  [br]x[/br] Obviously the drive got stuck and either its firmware or the operating system lost patience.  [br]x[/br]  Possible culprits are the data cable between drive and computer, and the drive itself. So if re-plugging and possibly exchanging of the cable does not help, you will probably need a new DVD drive.  [br]x[/br] -------------------------------------------------------- [br]x[/br]  The Brasero run yielded a different complaint from the drive (forwarded by my libburn):  >  BraseroLibburn Libburn reported an error SCSI error on write(16,16): [5 21 00] Illegal request.   "Logical block address out of range"  [br]x[/br]  The drive states that it is not possible to write to block 16 of the medium. [br]x[/br] Was this medium already used for a failed Nero run ?  [br]x[/br] [br]x[/br] If not - and if you do not exchange the drive - what messages do you get from this command line burn attempt:  ```
xorriso -as cdrecord -v dev=/dev/sr0 blank=as_needed /media/mandar/Software/ubuntu-14.04.2-server-amd64.iso 
```  (The drive address /dev/sr0 is guessed. If you got more than one DVD drive, find the desired one by  ```
xorriso -devices
```)  [br]x[/br] [br]x[/br]  Have a nice day :) [br]x[/br] Thomas

---

### Post by mandarpowale on 2015-02-26
My DVD drive is able to read and boot properly. How can the data cable or DVDRW be faulty then ?

I have 4GB Ram which is detected properly in UBUNTU DESKTOP 14.04 x64 UBUNTU, but only 3GB is used in my WinXP 32 bit.

I don't know for sure that it is a DVD-RW problem. I have wasted more than 3 cds and 3 dvds behind this burning effort. (Is there a fault with my settings in nero or brassero ?)

I also mounted the iso in winxp using daemon tools. It did not give the same feedback as UBUNTU 14.04 LTS desktop cd gives (which prompt's to install). So I think that the ISO may not be bootable at all. 

I downloaded the said iso using utorrent in windows.

I'm really sad and pissed.

---

### Post by scdbackup on 2015-02-26
Hi,  >  My DVD drive is able to read and boot properly. How can the data cable or DVDRW be faulty then ?  This decreases the chance that the cable is to blame. [br]x[/br] If the medium which failed with Brasero is a DVD+RW, then it cannot be to blame for the "error on write(16,16): [5 21 00] Illegal request. [br]x[/br] If it is a DVD-RW and not formatted, then the write error could be due to an incomplete burn state of the the medium. [br]x[/br] [br]x[/br]  The ISO image is surely not to blame for the SCSI errors reported by Nero and Brasero. >  So I think that the ISO may not be bootable at all.  Let's have a look:  ```
 wget http://releases.ubuntu.com/14.04/ubuntu-14.04-server-amd64.iso  
``` ```
xorriso -indev ubuntu-14.04-server-amd64.iso -pvd_info -report_el_torito plain -report_system_area plain
``` yields```
Preparer Id  : XORRISO-1.2.4 2012.07.20.130001, LIBISOBURN-1.2.4, LIBISOFS-1.2.4, LIBBURN-1.2.4 ... El Torito images   :   N  Pltf  B   Emul  Ld_seg  Hdpt  Ldsiz         LBA El Torito boot img :   1  BIOS  y   none  0x0000  0x00      4        8446 El Torito boot img :   2  UEFI  y   none  0x0000  0x00   4672       24754 El Torito img path :   1  /isolinux/isolinux.bin ...  El Torito img path :   2  /boot/grub/efi.img ... MBR partition table:   N Status  Type        Start       Blocks  MBR partition      :   1   0x80  0x00            0      1155072  MBR partition      :   2   0x00  0xef        99016         4672  MBR partition path :   2  /boot/grub/efi.img  ...  GPT start and size :   2  99016  4672  GPT partition path :   2  /boot/grub/efi.img ... APM partition path :   1  /boot/grub/efi.img 
```(Sorry for the missing line breaks here. This forum software is somewhat tricky.) [br]x[/br] [br]x[/br] It will boot from CD/DVD/BD and from hard disk-like devices (e.g. USB stick). It will boot via BIOS firmware (old PC style) by help of ISOLINUX and via UEFI (new 64 bit PCs) by help of GRUB2. [br]x[/br] [br]x[/br]  Since your DVD burner refuses to burn, you could try an USB stick or some external hard disk. [br]x[/br] If you already have a Unix-like operating system then do in a shell session (e.g. in an xterm window), what is described in [http://www.syslinux.org/wiki/index.php/Isohybrid#Copying_onto_USB_stick_by_shell_commands](http://www.syslinux.org/wiki/index.php/Isohybrid#Copying_onto_USB_stick_by_shell_commands)  >  I'm really sad and pissed.  I'm with you. But probably you will not be able to avoid exchanging the burner drive. [br]x[/br] The Nero symptoms clearly point to the hardware. Beginning at the SATA or PATA bus controller of your computer and ending at the burn drive's opto-electronic components. [br]x[/br] The Brasero symptom would also match a CD-R[W], DVD-R[W], or DVD+R which was already incompletely written. (A burn attempt with xorriso might tell more.) [br]x[/br] [br]x[/br]  Have a nice day :) [br]x[/br] [br]x[/br]  Thomas

---

### Post by mandarpowale on 2015-02-26
I finally took my iso to a service provider(our local xerox shop) and got it burnt using nero express. it boots successfully now. my boot area mbr might be to blame. because i see two same options to boot from xp, which i had previously installed. how to repair the boot area ? (grub loader)?

My system config is

Amd Ahtlon II X2 260,
4GB DDR III 1333MHZ GSKILL
ASUS M4N68T-M LE V2
ASUS HD7750-1GD5 V2
1 TB WD PURPLE(250 GB Win XP 32bit, 30 GB '/', 16 GB SWAP , 200 GB '/home', 460 GB NTFS)
500 GB WD GREEN(146 GB Bad Sector, 146 GB Good, 172 GB Good)
CIRCLE 500W PSU (RAW POWER)
ASUS DRW-24B5ST.

I had previouly installed winxp on C: ubuntu on 1tb, E: 400GB for various backups and softwares. (all this on 1 tb)
D: was my previous windows (pirated) which developed bad sectors,F:  146 GB good data partition and G:172 GB good data partition
I formated the previous version of ubuntu from xp(legit) (XP C: , E: UBUNTU dual boot)and it caused booting failure. 
Then I installed XP on F: 
Finally i deleted everything on 1tb and reinstalled XP fresh and UBUNTU fresh. But the F: entry has to be removed.

Please help with that.

12 Optical disks have gone to waste during my efforts. :( :(

Hey guys , Just gonna buy new DVD writer tomorrow.

I thought that my settings were wrong or my WinXP was faulty.

I wasted about 15 optical discs with various softwares.

---

### Post by mörgæs on 2015-02-26
In post #4 you were advised to use a USB stick.

---

### Post by mandarpowale on 2015-02-26
Hello, I need some help

I tried making a bootable USB out of ubuntu 14.04.2 server's iso which i downloaded using utorrent on my xp partition.

In windows xp sp3  i tried Rufus to make the bootable dvd (it failed the integrity check)

In my UBUNTU 14.04 desktop edition i tried making the usb using startup disk creator (that fails the integrity check too)

I managed to get the iso burned on CD and that works just super when it comes to integrity check.

Please tell me what is it that i'm doing wrong in the process of making a bootable USB,

If you need any more info please ask.

My mobo is M4N68T-M LE-V2 with BIOS updated to its latest version.

---

### Post by tgalati4 on 2015-02-26
When burning CD's or DVD's, you have a better chance of a clean copy by using the slowest write speed possible.  Quality of the media is also important.  It's not uncommon to have several bad burns before you get a decent one.  Some DVD writers (LG and Sony and others with Sony lasers) have defective lasers that corrode over time, so if you can't burn anything, do a search for your model.  It's a pretty common occurance.

For making a USB, *unetbootin* works as well as USB Creator (*usb-creator-gtk* or *usb-creator-kde*) under linux.

Open a terminal:

```
sudo apt-get install unetbootin
unetbootin
```

It's a good idea to inspect the checksum of the image that you have downloaded as well as run the integrity check on the booted disk/stick itself.  Failure to do so can result in pain.

Don't go crazy with a USB stick.  Don't put 12 partitions on it.  Put 2, make the first one FAT32 and the second one ext2 or FAT32 as well.  Put the boot image on the first partition.

---

### Post by mandarpowale on 2015-02-26
> **mörgæs said:**
> In post #4 you were advised to use a USB stick.

How do I make a bootable USB of Ubuntu 14.04 Server LTS iso using command line or gui of and 'startup disk creator'

When I tried the verify CD integrity test fails.

---

### Post by mandarpowale on 2015-02-26
I want to use only linux inbuilt gui tools like 'Startup Disk Creator'. My DVD writer is ASus DRW-24B5ST.

Is making partitions in pendrives mandatory ?

Unable to use unetbootin due to lack of technical knowledge.

[COLOR=#000000]Is making partitions in pendrives mandatory ? I don't think so cuz my ubuntu desktop edition got into the stick just perfect.

Im redownloading the server file iso.[/COLOR]

---

### Post by tgalati4 on 2015-02-26
If you have a 4 GB stick and you load a 2 GB ISO, then you have wasted 2 GB.  So, you can create two partitions of 2 GB each and the second partition will show up as a data drive--which is handy for loading drivers, moving files, etc.

Of course, you must make sure that the partition that you create is big enough to hold the ISO image.

[Unetbootin]("https://help.ubuntu.com/community/UNetbootin") is not difficult to use.

---

### Post by mörgæs on 2015-02-27
> **mandarpowale said:**
> How do I make a bootable USB of Ubuntu 14.04 Server LTS iso using command line or gui of and 'startup disk creator'


There are many guides available. One of them is
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)

> **mandarpowale said:**
> 
When I tried the verify CD integrity test fails.
Forget about CD's and DVD's for now. They are an emergency solution if the USB stick does not work.

---

### Post by slickymaster on 2015-02-27
Threads merged.

Please do not create duplicate threads, it dilutes the community&#8217;s efforts to provide support and causes confusion.

---

### Post by mandarpowale on 2015-02-27
> **mörgæs said:**
> There are many guides available. One of them is
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)


Forget about CD's and DVD's for now. They are an emergency solution if the USB stick does not work.

hi!,

I tried 'check disk integrity' while booting from Bootable USB of server 14.04 LTS. I use Rufus 1.4.12. (the desktop edition passes the test)

I hope you can find a solution.

Ty in advance,


Mandar

---

### Post by mattharris4 on 2015-03-09
> **tgalati4 said:**
> 
```
sudo apt-get install unetbootin
unetbootin
```

It's a good idea to inspect the checksum of the image that you have downloaded as well as run the integrity check on the booted disk/stick itself.  Failure to do so can result in pain.

Don't go crazy with a USB stick.  Don't put 12 partitions on it.  Put 2, make the first one FAT32 and the second one ext2 or FAT32 as well.  Put the boot image on the first partition.

I use Unetbootin to make up USB sticks as well, the process is actually pretty automatic after ensuring that it isn't attempting to write to your hard drive (bottom line of Unetbootin window).  

I would not use the terminal to install it, however unless you are VERY experienced with using a Linux terminal -- especially since it requires using a sudo command (essentially opening the computer up to any command which IMO is trouble to those unknowing although sometimes unfortunately necessary to do) which if you mistype could theoretically cause you to create very severe damage to your Ubuntu installation.  Unetbootin is available through the Ubuntu Software Center, search for it there and follow the install process.  If you aren't running Ubuntu you can install the Ubuntu Software Center through whatever software center is on your Canonical OS if need be (Lubuntu Software Center, etc.) -- in this case if Unetbootin were not available through that OSes native Software Center.

---

