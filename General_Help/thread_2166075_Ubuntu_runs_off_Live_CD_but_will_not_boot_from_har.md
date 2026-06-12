---
title: "Ubuntu runs off Live CD but will not boot from hard drive 13.04"
date: 2013-08-07
forum: General Help
---

### Post by Bryce_Crist on 2013-08-07
I installed Ubuntu a couple days ago. I got it to boot (after tons of trouble), and it seemingly worked fine. However, after troubles with my HDMI (no sound) and presumably my AMD drivers, I decided to install a proprietary driver for AMD Catalyst, which in turn made Ubuntu unusable. To combat this problem, I had Ubuntu delete the old install and reinstall itself. This time, however, I cannot seem to get it to boot correctly. I can boot using the trial from the Live CD, but without the CD I cannot access Ubuntu. I've tried Boot Repair (which for some reason in its *advanced options* section all of the other options were unavailable to me) and restarted -- that didn't work. Next, I tried to reinstall, once again deleting the old Ubuntu, and still had no luck. I thought maybe my Bios settings were screwing it up, but everything is set so the hard drive boots first. I'm not exactly sure what else I should do.

My PC Specs:  
HP tower model: h8-1210t  
RAM/Memory: 6Gib (5951Mib)  
Processor: Intel(R) Core(TM) i5-2320 CPU @ 3.00GHz  
Video Card: Radeon HD 7450
Current installed Ubuntu version: 13.04  
Hard Drive Space: 1Tib (921Gib)

I'm not entirely sure what else I should post regarding specs, but I can post any info you need me to if you ask. I've pretty much given up on Ubuntu at this point. It is very lovely, don't get me wrong, but there are sooo many bugs and I can't get anything to work right. If I could, I would love to keep it, but I keep running into problems. Like mentioned before, my HDMI cable. I play a lot of Netflix off my computer, and I have a TV connected via HDMI to my desktop. I am able to get Netflix up and running, everything looks great, but there is no sound being outputted from my TV. The HDMI cable isn't listed in my PulseAudio, nor my regular audio settings. However, this is a problem for a separate thread I suppose. I wish I could just get things to work. I updated the kernel, updated ALSA to the daily build, and everything.. *sigh*


EDIT: I was browsing some other answers and decided to input the code  

    sudo grub-install /dev/sda
    
What I got was an error code saying this:

    Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.

I'm not sure if that means anything to you guys, but I thought maybe it'd help identify the error better.

---

### Post by Bryce_Crist on 2013-08-07
I tried using Gparted to mess with things, but I have no idea what I'm doing. I took a screen shot, maybe there's some information here that you guys might need.




[IMG]http://i.imgur.com/cj8j2hB.png[/IMG]

---

### Post by carl4926 on 2013-08-07
Start again and take a look at this: [https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/13_04_slideshow.pdf](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/13_04_slideshow.pdf)

---

### Post by Bryce_Crist on 2013-08-07
Thanks for the reply. I looked at the slide show. When I choose "something else" at the installation menu and go on to  continue, I get an error of some sort -- something about the "/boot" I think. I wasn't ever able to continue from that menu, so I went back and installed it using the other options.

---

### Post by Bryce_Crist on 2013-08-07
I could try reinstalling again?

---

### Post by Bryce_Crist on 2013-08-07
Well... if anyone else could help me out that'd be great. I took some pictures of my screen during the installation process. 

This is the screen shown when I click "somthing else."

[IMG]http://imgur.com/288TATM.jpg[/IMG]



This is the menu I get when I click "change." Unlike the slide show, I am not given the option to format the partition. 

[IMG]http://imgur.com/QIVqw1I.jpg[/IMG]


This is the error screen I get once I click "install now." 

[IMG]http://imgur.com/N3EtL2m.jpg[/IMG]


If any of you could give me advice as to what to do, I'd really appreciate it.

---

### Post by Bryce_Crist on 2013-08-07
Okay, still no help from anyone. I went back into the "something else" section. I set the mount point of /dev/sda to */* and the type of /dev/sda3 to *swap* and kept /dev/sda1 as *efi* because I couldn't raise the size to allow a mount point for */*.

It installed, but I still have issues booting without the Live CD. 

Here's an updated look at Gparted

[IMG]http://i.imgur.com/fh3JiaE.png[/IMG]

---

### Post by Bryce_Crist on 2013-08-07
I also just ran boot repair, once again. Here is the pastebin log it gave me:

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 6Aug2013]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       391,167       389,120 EFI System partition
/dev/sda2         391,168       890,879       499,712 Swap partition (Linux)
/dev/sda3         890,880 1,953,523,711 1,952,632,832 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        cdf62972-cc7b-4385-8f1e-2292c09a7e88   ext2       
/dev/sda2        8020f32a-f2c0-4d08-a27c-3f1fb0ebf5ef   swap       
/dev/sda3        45a9a2e8-e8a6-4a0c-acd2-e9e732de498c   crypto_LUKS 
/dev/sr0                                                iso9660    Ubuntu 13.04 amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  78 74 73 2d 70 6c 61 69  |........xts-plai|
00000030  6e 36 34 00 00 00 00 00  00 00 00 00 00 00 00 00  |n64.............|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 10 00 00 00 00 40  |...............@|
00000070  a5 3d 6b 83 0a bc 83 94  08 5d 36 86 0d d0 dd 58  |.=k......]6....X|
00000080  c5 9e b2 3a 19 22 fe 18  b1 68 59 9d 9e 27 0c ce  |...:."...hY..'..|
00000090  ca ba fc 53 07 f7 95 56  23 32 21 d2 70 fd c9 93  |...S...V#2!.p...|
000000a0  54 7d 75 58 00 00 e8 e9  34 35 61 39 61 32 65 38  |T}uX....45a9a2e8|
000000b0  2d 65 38 61 36 2d 34 61  30 63 2d 61 63 64 32 2d  |-e8a6-4a0c-acd2-|
000000c0  65 39 65 37 33 32 64 65  34 39 38 63 00 00 00 00  |e9e732de498c....|
000000d0  00 ac 71 f3 00 03 a4 58  d9 a6 f4 fc a7 b7 a2 f5  |..q....X........|
000000e0  fa e2 db 42 2f 02 8c 11  ce a1 c6 7b 08 93 27 48  |...B/......{..'H|
000000f0  9a 89 ef ee 81 dd b0 ef  00 00 00 08 00 00 0f a0  |................|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 02 00 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 03 f8 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 05 f0 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 07 e8 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 09 e0 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

File descriptor 8 (/proc/4922/mounts) leaked on lvscan invocation. Parent PID 10014: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-08-07__21h01 ===================
boot-repair version : 3.199~ppa10~raring
boot-sav version : 3.199~ppa10~raring
glade2script version : 3.2.2~ppa45~raring
boot-sav-extra version : 3.199~ppa10~raring
boot-repair is executed in live-session (Ubuntu 13.04, raring, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
mount: unknown filesystem type 'crypto_LUKS'
mount /dev/sda3 -> Error code 32

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="cdf62972-cc7b-4385-8f1e-2292c09a7e88" TYPE="ext2"
/dev/sda2: UUID="8020f32a-f2c0-4d08-a27c-3f1fb0ebf5ef" TYPE="swap"
/dev/sda3: UUID="45a9a2e8-e8a6-4a0c-acd2-e9e732de498c" TYPE="crypto_LUKS"
/dev/sr0: LABEL="Ubuntu 13.04 amd64" TYPE="iso9660"

mount: unknown filesystem type 'crypto_LUKS'
mount /dev/sda3 -> Error code 32

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

ls /sys/firmware/efi/vars : UsbSupport-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,USB_POINT-8be4df61-93ca-11d2-aa0d-00e098032b8c,UsbMassDevValid-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,UsbMassDevNum-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,ucal-707c9176-a4c1-4e27-851d-1c37b7ca73c8,Timeout-8be4df61-93ca-11d2-aa0d-00e098032b8c,SystemIds-71202eee-5f53-40d9-ab3d-9e0c26d96657,StdDefaults-4599d26f-1a11-49b8-b91f-858745cff824,Setup-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,SetupCpuFeatures-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,SerialPortsEnabledVar-560bf58a-1e0d-4d7e-953f-2980a261e031,RBLastBoot-24b0699b-65a9-4e12-9a81-21d719c2d390,RBCheckSumTbl-58ae1a7f-513b-45cc-8b36-f5b158192e86,PowerOnTime-0b181fb7-e53e-4af5-a67d-7ac2de7e3e50,PlatformLangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c,PlatformLang-8be4df61-93ca-11d2-aa0d-00e098032b8c,PEGAControlVariables-3e82bad6-1848-46fa-9d12-ab72b5249192,PciSerialPortsLocationVar-560bf58a-1e0d-4d7e-953f-2980a261e031,OldLegacyDevOrder-a56074db-65fe-45f7-bd21-2d2bdd8e9652,new_var,NBMemoryInfo-490216c0-076a-44d3-a536-ace05c90e386,MrcS3Resume-6737934b-a27e-4c05-ad5b-6ab86273680b,MonotonicCounter-8be4df61-93ca-11d2-aa0d-00e098032b8c,MemCeil.-8be4df61-93ca-11d2-aa0d-00e098032b8c,LegacyDevOrder-a56074db-65fe-45f7-bd21-2d2bdd8e9652,LastMemorySize-fae1c30d-0113-4946-9504-1c63af98b923,LangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c,Lang-8be4df61-93ca-11d2-aa0d-00e098032b8c,HpSaveBootOrder-8be4df61-93ca-11d2-aa0d-00e098032b8c,HpPreviousBoot-8be4df61-93ca-11d2-aa0d-00e098032b8c,HpPassphraseStructureVariable-707c9176-a4c1-4e27-851d-1c37b7ca73c8,HddDevice-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,HDD14-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,HDD13-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,HDD12-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,HDD11-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,HDD10-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,HDD09-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,HDD08-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,HDD07-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,HDD06-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,HDD05-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,HDD04-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,HDD03-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,HDD02-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,HDD01-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,HDD00-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,FLOPPYDEVICE-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,FLOPPY02-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,FLOPPY01-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,FLOPPY00-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,FeatureByteVt-f189629f-a25e-44ba-91e1-18ac7c7de02c,FBYTEVariableSbso-f189629f-a25e-44ba-91e1-18ac7c7de02c,FBYTEVariableNoLogo-f189629f-a25e-44ba-91e1-18ac7c7de02c,FBYTEVariableIntSPK-f189629f-a25e-44ba-91e1-18ac7c7de02c,FBYTEVariable-f189629f-a25e-44ba-91e1-18ac7c7de02c,ErrOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ErrOut-8be4df61-93ca-11d2-aa0d-00e098032b8c,EfiTime-9d0da369-540b-46f8-85a0-2b5f2c301e15,DmiVarbf-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarbe-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarbd-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarbc-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarbb-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarba-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb9-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb8-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb7-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb6-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb5-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb4-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb3-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb2-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb1f-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb1e-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb1d-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb1c-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb1b-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb1a-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb19-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb18-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb17-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb16-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb15-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb1-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb14-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb13-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb12-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb11-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb10-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVarb0-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar38-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar37-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar27-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar18-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar17-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar15-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiVar119-4b3082a3-80c6-4d7e-9cd0-583917265df1,DmiArray-4b3082a3-80c6-4d7e-9cd0-583917265df1,del_var,CpuS3Resume-30b98b95-dfa3-4501-a3ce-e38c186384a0,ConOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConOut-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConInDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConIn-8be4df61-93ca-11d2-aa0d-00e098032b8c,CDROMDEVICE-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,CDROM06-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,CDROM05-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,CDROM04-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,CDROM03-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,CDROM02-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,CDROM01-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,CDROM00-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,BuildIdDdc-f115d093-962a-4d58-8ccb-764517382460,BootSource-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootOrder-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootCurrent-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot000a-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0009-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0008-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0007-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0006-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0005-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0002-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0001-8be4df61-93ca-11d2-aa0d-00e098032b8c,AmlBufMemAddr-8be4df61-93ca-11d2-aa0d-00e098032b8c,AMITSESetup-c811fa38-42c8-4579-a9bb-60e94eddfb34,AcpiGlobalVariable-af9ffd67-ec10-488a-9dfc-6cbf5ee22c2e,
Please report this message to [email]boot.repair@gmail.com[/email]
efibootmgr -v
gui-g2slaunch.sh: line 156: efibootmgr: command not found
=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot maybe enabled. (maybe sec-boot, Please report this message to [email]boot.repair@gmail.com[/email])


=================== PARTITIONS & DISKS:
sda1	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sda3	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda3.

sda	: GPT,	no-BIOS_boot,	has-no-EFIpart, 	not-usb,	no-os,	2048 sectors * 512 bytes


=================== parted -l:

Model: ATA ST31000524AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
1      1049kB  200MB   199MB   ext2                  boot
2      200MB   456MB   256MB   linux-swap(v1)
3      456MB   1000GB  1000GB  ext2



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Can't have a partition outside the disk!

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:512:gpt:ATA ST31000524AS;
1:1049kB:200MB:199MB:ext2::boot;
2:200MB:456MB:256MB:linux-swap(v1)::;
3:456MB:1000GB:1000GB:ext2::;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Can't have a partition outside the disk!


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/ubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type ext2 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdc sdd sde sg0 sg1 sg2 sg3 sg4 sg5 shm snapshot snd sr0 stderr stdin stdout uinput urandom usb vga_arbiter vhost-net zero
ls /dev/mapper:  control

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  3.0G  106M  2.9G   4% /
udev           devtmpfs   2.9G   12K  2.9G   1% /dev
tmpfs          tmpfs      596M  864K  595M   1% /run
/dev/sr0       iso9660    785M  785M     0 100% /cdrom
/dev/loop0     squashfs   738M  738M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      3.0G  1.1M  3.0G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      3.0G   76K  3.0G   1% /run/shm
none           tmpfs      100M   40K  100M   1% /run/user
/dev/sda1      ext2       184M  1.6M  173M   1% /mnt/boot-sav/sda1

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT


No OS or WinEFI system

=================== Default settings
Recommended-Repair
This setting would not act on the MBR.
Additional repair would be performed:  repair-filesystems

=================== Settings chosen by the user
Custom-Repair
This setting will not act on the MBR.
Additional repair will be performed:  repair-filesystems


Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


fsck -fyM /dev/sda1
fsck from util-linux 2.20.1

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


fsck -fyM /dev/sda3
fsck from util-linux 2.20.1
fsck: fsck.crypto_LUKS: not found
fsck: error 2 while executing fsck.crypto_LUKS for /dev/sda3
mount: unknown filesystem type 'crypto_LUKS'
mount /dev/sda3 -> Error code 32

Boot successfully repaired.

You can now reboot your computer.

---

### Post by ajgreeny on 2013-08-07
There is no need to do anything with the first partition, the 199MB EFI partition; just leave it as it is. This presumes you have a UEFI system and are booting the DVD in UEFI mode.  If you do not boot the install medium in UEFI mode you will not be able to install in UEFI mode successfully, though you could do away with the UEFI and boot and install in legacy mode if you preferred.

If using UEFI, in the installer, "Something Else" go to partitions, sda2 and sda3 and delete them, unless you know of some files on them that you need; if so you can copy them to a USB drive using the live DVD.  Come back for details of how to do that if you're not sure how.  Having deleted those partitions, I suggest you create three new ones.
[LIST=1]
[*]20 -25GB as ext4, and with / as mountpoint.  This is your root partition, and will be sda2 if you have kept the EFI partition. Your latest attempt with gave /dev/sda as root will never work; you must give it a number.  I am not even sure how you managed to give /dev/sda a mountpoint, as it is not even a partition, but that's for another time. 
[*]4 - 8GB as swap, with no mountpoint needed. 
[*]The remainder as ext4, and with /home as the mountpoint. 
[/LIST]

You most recent post saying you have deleted the EFI partition adds to my uncertainties about what your current position is, and whether or not you are using UEFI mode to install, so come back again if this all makes no sense to you at all, and we'll try to help further.

For all info about UEFI vs legacy (BIOS) mode installation see [URL="https://help.ubuntu.com/community/UEFI"]UEFI - Ubuntu Documentation
[/URL]
EDIT:
Just seen your post about boot-repair.  Did it help? I suspect not.
You big problem is probably not having dealt with the UEFI system properly, so read my linked page above and try to follow what it says there exactly.

---

### Post by Bryce_Crist on 2013-08-07
I very much appreciate your reply. I have no idea what UEFI is. I'll reinstall using the steps you have give nme.

---

### Post by Bryce_Crist on 2013-08-07
How do I create new partitions? It isn't giving me the option unless I click on /dev/sda. If I choose to create new partitions on the /dev/sda, it deletes the old ones and doesn't allow me to create anything.

EDIT: I figured out how, I apologize. I'll update the partitions and post a screenshot.

---

### Post by Bryce_Crist on 2013-08-07
Do I have everything setup correctly?


[IMG]http://i.imgur.com/xOpmVcx.png[/IMG]

---

### Post by Bryce_Crist on 2013-08-07
Okay, I reread your post ajgreeny and noticed you said to leave the efi, so I edited the partitions a bit a mad an efi with 1000Mib. Does this look any better?  


[IMG]http://i.imgur.com/7PdgFD2.png[/IMG]

---

### Post by ajgreeny on 2013-08-07
You now have no EFI partition, the old 199MB sda1 that you saw originally, and we still don't know if you are trying to install in UEFI or legacy BIOS mode.  It is imperative that if you boot the DVD and install in UEFI mode you must have that EFI partition; you must get that step correct or you will get nowhere.

Read again that UEFI link I gave and it tells you how to work out what your machine is set to, UEFI or legacy BIOS.

---

### Post by Bryce_Crist on 2013-08-07
I check and it says I'm booting with EFI, so I think I'm good. 

[IMG]http://i.imgur.com/QLoi2NY.png[/IMG]

---

### Post by Bryce_Crist on 2013-08-07
Okay, I added the EFI partition, and I am installing in UEFI mode. Should I go ahead and run the install?

---

### Post by Bryce_Crist on 2013-08-07
I organized it a bit more, with the efi pardon at the beginning. To be clear, you said to set the remaining space (the other 900+ Gib) as mount point */home* (/dev/sda4)?

[IMG]http://i.imgur.com/zodVhDS.png[/IMG]

---

### Post by Bryce_Crist on 2013-08-07
Okay, well.. I reinstalled using the directions you gave me and I still can't get a correct boot. Here are the partitions from Gparted. 


[IMG]http://i.imgur.com/ZRKtAf3.png[/IMG]

---

### Post by Bryce_Crist on 2013-08-07
I'm gonna hit it one more time with boot repair, and let you know if it worked. It would be cool if you could reply a bit faster, so we can troubleshoot the problem. Thanks for trying to help me out.

---

### Post by Bryce_Crist on 2013-08-07
Okay, ajgreeny, I really need you to reply man. I tried to fix it with boot repair, but got this error message. Any ideas? 



[IMG]http://i.imgur.com/UvQH6fd.png[/IMG]

---

### Post by Bryce_Crist on 2013-08-07
Okay, @ajgreeny. I solved the problem. I appreciate the information you gave me, however, you could've been more helpful. Basically, what I did to get it to work is:

1. Opened up the installer, when to "something else" and reapplied the partitions shown a a couple screenshots ago. However, this time I added a "Bios-boot" partition right after the efi partition (as boot-repair wouldn't work without it as shown above).
2. Went through with the installation and rebooted my computer -- still no boot.
3. Loaded up Boot-repair and tried running it -- it gave me an error saying that both efi and Bios-boot were partitions.
4. Opened up Gparted and deleted the Bios-boot.
5. Went back to Boot-repair and chose to purge and reinstall grub. It worked this time.
6. Rebooted the computer and Ubuntu booted w/o the disk.

My solution may have been a special case. However, I got it to work. Maybe someone else will get some usefull information from this thread.

---

### Post by Iowan on 2013-08-07
> **Bryce_Crist said:**
> ... however, you could've been more helpful...Demand a refund...

---

### Post by carl4926 on 2013-08-07
A GPT table requires a bios_grub partition
[http://paste.opensuse.org/8183518](http://paste.opensuse.org/8183518)

Switching to a MBR DOS table would remove this requirement.  I'm not sure what is required with your secure boot settings in this situation.

---

### Post by ajgreeny on 2013-08-08
I am glad you got things to work eventually, and I am also sorry I could not answer your questions quicker, but I'm afraid I have to sleep and go to work sometimes, and as it happens, I could not have helped with your situation any more, as I know nothing about having a bios_grub partition.  My UEFI installed Xubuntu 12.04 on GPT partitions which is not dual boot has just 4 partitions, and it all worked straight away after installing:-

sda1 EFI fat32 200MB
sda2 / (root) ext4 20GB
sda3 /home ext4 980GB
sda4 swap 8GB (I use hibernate occasionally, hence 8GB swap to equal my ram.)

I have no idea if having a dual boot system means you have this extra bios_grub partition, or even if you still have it on your system as your final post is a bit confusing

---

