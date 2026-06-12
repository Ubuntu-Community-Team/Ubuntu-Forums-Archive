---
title: "I think I broke ubuntu, im new"
date: 2013-02-15
forum: General Help
---

### Post by Smirwarf on 2013-02-15
New to Ubuntu/Linux, have always used Windows since I got my first pc as a little kid.  I have a laptop that I want to use strickly for playing my movies and playing my ROMs.  I heard that Windows uses a lot of RAM compared to Linux so i wanted to try it out.

When i got it all working I started to love the look of it but couldnt get to my movies folder. Said something bout unable to mount my harddrive.  I did a google search and found a forum where this guy said to type all this stuff into the fstab or something (im really a nub at this) and it will link my hardrive to Ubuntu and I would be able to access all my files from Windows threw Ubuntu.

Well after doing a restart which was the final step Ubuntu shows the purple screen and than goes black and doesnt look like its doing anything at all.  Im thinking of just uninstalling and reinstalling, but does anyone have any advice as to what happened and also an easier noob friendly way of being able to access my movies threw Ubuntu?

---

### Post by Bufeu on 2013-02-15
You should not edit /etc/fstab unless you know what you are doing.
If you have Ubuntu on a CD or USB, boot the computer from that. Open up a Terminal, type in ```
sudo blkid
```and then press Enter. Copy and paste the output of the command here. Please use the [CODE]-tag.

---

### Post by Bufeu on 2013-02-15
And please, post the output from ```
cat /etc/fstab
```as well.

EDIT: I mean the fstab on your drive, not on the live-CD. You drive(s) should be mounted automatically. Take a look at the folder *etc* in the drive and post the contain of the file *fstab*.

---

### Post by grahammechanical on 2013-02-15
There is something that I do not understand. You say that you have installed Ubuntu and it is working fine. But you cannot access your movies folder and you get the message 'cannot mount hard drive.'

Please give more details on the hardware. Do you have more than one hard drive? where is this movies folder? On the same hard drive as Ubuntu? Or on another hard drive that has Windows on it?  Please explain your set up.

Regards.

---

### Post by schragge on 2013-02-15
I understand it so that the movie folder is on Windows, and the OP tried to get the Windows partition mounted automatically on Ubuntu, but busted the */etc/fstab* and now Ubuntu doesn't start. Am I right?

---

### Post by Bufeu on 2013-02-15
> **schragge said:**
> I understand it so that the movie folder is on Windows, and the OP tried to get the Windows partition mounted automatically on Ubuntu, but busted the */etc/fstab* and now Ubuntu doesn't start. Am I right?
Yeah, but we can "repair" it. Give us the output of ```
sudo blkid
```

---

### Post by Smirwarf on 2013-02-15
```
/dev/sda1: LABEL="System" UUID="001C4BB61C4BA60E" TYPE="ntfs" 
/dev/sda3: LABEL="HDDRECOVERY" UUID="C67698B17698A3A9" TYPE="ntfs" 
/dev/loop0: UUID="a6eece84-8179-4998-be7d-08085c5290d4" TYPE="ext3" 
/dev/sda2: LABEL="TI106319W0D" UUID="BCB87243B871FC68" TYPE="ntfs" 
smirwarf@ubuntu:~$ cat /etc/fstab
# UNCONFIGURED FSTAB FOR BASE SYSTEM
/host/ubuntu/disks/swap.disk    none    swap    sw    0    0
smirwarf@ubuntu:~$ 

```think i did that right lol anyhow i typed out and pasted everything it said here.

btw i just got the windows installer file and installed it that way, i didnt do anything else  but let the installer do its thing and click the ok buttons lol i just reinstalled Ubuntu also so i can now get into it again.  But still would really like to know how to get to my movies which are on the Windows part of the machine, if im understanding this right >_<

---

### Post by Bufeu on 2013-02-15
Ah, you reinstalled Ubuntu.
OK. You want to mount the drive in Ubuntu, right? Please answer the questions **grahammechanical** asked. We need more information about your setup.

---

### Post by Smirwarf on 2013-02-15
Yea just wana be able to watch my movies in Ubunto, ill be posting my system here in a min. I left my laptop for a bit and it went into standby mode and got the Black Screen again and wouldnt wake up, had to restart the whole system lol I just really dont wana use Windows anymore cept for my college stuff, Ubuntu is gonna be what i use to play my roms and movies, I just think it looks alot "cooler" than windows lol

ok here is the info of my system:

```

------------------
System Information
------------------
Time of this report: 2/15/2013, 13:52:59
       Machine name: SMIRWARF-PC
   Operating System: Windows 7 Home Premium 64-bit (6.1, Build 7601) Service Pack 1 (7601.win7sp1_gdr.120830-0333)
           Language: English (Regional Setting: English)
System Manufacturer: TOSHIBA
       System Model: Satellite C675D
               BIOS: BIOS Date: 07/01/11 16:44:54 Ver: 04.06.04
          Processor: AMD E-300 APU with Radeon(tm) HD Graphics (2 CPUs), ~1.3GHz
             Memory: 4096MB RAM
Available OS Memory: 3694MB RAM
          Page File: 1768MB used, 18923MB available
        Windows Dir: C:\windows
    DirectX Version: DirectX 11
DX Setup Parameters: Not found
   User DPI Setting: Using System DPI
 System DPI Setting: 96 DPI (100 percent)
    DWM DPI Scaling: Disabled
     DxDiag Version: 6.01.7601.17514 64bit Unicode
  DxDiag Previously: Crashed in DirectSound (stage 1) & DirectShow (stage 1). Re-running DxDiag with "dontskip" command line parameter or choosing not to bypass information gathering when prompted might result in DxDiag successfully obtaining this information

------------
DxDiag Notes
------------
      Display Tab 1: No problems found.
          Input Tab: No problems found.

--------------------
DirectX Debug Levels
--------------------
Direct3D:    0/4 (retail)
DirectDraw:  0/4 (retail)
DirectInput: 0/5 (retail)
DirectMusic: 0/5 (retail)
DirectPlay:  0/9 (retail)
DirectSound: 0/5 (retail)
DirectShow:  0/6 (retail)

---------------
Display Devices
---------------
          Card name: AMD Radeon HD 6310 Graphics         
       Manufacturer: ATI Technologies Inc.
          Chip type: ATI display adapter (0x9802)
           DAC type: Internal DAC(400MHz)
         Device Key: Enum\PCI\VEN_1002&DEV_9802&SUBSYS_FD741179&REV_00
     Display Memory: 1966 MB
   Dedicated Memory: 375 MB
      Shared Memory: 1590 MB
       Current Mode: 1600 x 900 (32 bit) (60Hz)
       Monitor Name: Generic PnP Monitor
      Monitor Model: unknown
         Monitor Id: AUO139E
        Native Mode: 1600 x 900(p) (60.112Hz)
        Output Type: Internal
        Driver Name: aticfx64.dll,aticfx64.dll,aticfx64.dll,aticfx32,aticfx32,aticfx32,atiumd64.dll,atidxx64.dll,atidxx64.dll,atiumdag,atidxx32,atidxx32,atiumdva,atiumd6a.cap,atitmm64.dll
Driver File Version: 8.17.0010.1083 (English)
     Driver Version: 8.862.0.0
        DDI Version: 11
       Driver Model: WDDM 1.1
  Driver Attributes: Final Retail
   Driver Date/Size: 6/7/2011 23:58:16, 811008 bytes
        WHQL Logo'd: Yes
    WHQL Date Stamp: 
  Device Identifier: {D7B71EE2-DB42-11CF-F276-7EDDBEC2C535}
          Vendor ID: 0x1002
          Device ID: 0x9802
          SubSys ID: 0xFD741179
        Revision ID: 0x0000
 Driver Strong Name: oem3.inf:ATI.Mfg.NTamd64.6.1:ati2mtag_Wrestler:8.862.0.0:pci\ven_1002&dev_9802&subsys_fd741179
     Rank Of Driver: 00E60001
        Video Accel: ModeMPEG2_A ModeMPEG2_C 
   Deinterlace Caps: {6E8329FF-B642-418B-BCF0-BCB6591E255F}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,1) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                     {6E8329FF-B642-418B-BCF0-BCB6591E255F}: Format(In/Out)=(UYVY,UYVY) Frames(Prev/Fwd/Back)=(0,0,1) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(UYVY,UYVY) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(UYVY,UYVY) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(YV12,0x32315659) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {552C0DAD-CCBC-420B-83C8-74943CF9F1A6}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,2) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                     {6E8329FF-B642-418B-BCF0-BCB6591E255F}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,1) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(IMC1,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(IMC2,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(IMC3,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(IMC4,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(S340,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(S342,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
       D3D9 Overlay: Not Supported
            DXVA-HD: Not Supported
       DDraw Status: Enabled
         D3D Status: Enabled
         AGP Status: Enabled

-------------
Sound Devices
-------------
---------------------
Sound Capture Devices
---------------------
-------------------
DirectInput Devices
-------------------
      Device Name: Mouse
         Attached: 1
    Controller ID: n/a
Vendor/Product ID: n/a
        FF Driver: n/a

      Device Name: Keyboard
         Attached: 1
    Controller ID: n/a
Vendor/Product ID: n/a
        FF Driver: n/a

      Device Name: Microsoft Hardware USB Mouse
         Attached: 1
    Controller ID: 0x0
Vendor/Product ID: 0x045E, 0x0745
        FF Driver: n/a

      Device Name: Micr
         Attached: 1
    Controller ID: 0x0
Vendor/Product ID: 0x045E, 0x0745
        FF Driver: n/a

      Device Name: Micr
         Attached: 1
    Controller ID: 0x0
Vendor/Product ID: 0x045E, 0x0745
        FF Driver: n/a

      Device Name: Micr
         Attached: 1
    Controller ID: 0x0
Vendor/Product ID: 0x045E, 0x0745
        FF Driver: n/a

      Device Name: Micr
         Attached: 1
    Controller ID: 0x0
Vendor/Product ID: 0x045E, 0x0745
        FF Driver: n/a

Poll w/ Interrupt: No

-----------
USB Devices
-----------
+ USB Root Hub
| Vendor/Product ID: 0x1002, 0x4397
| Matching Device ID: usb\root_hub
| Service: usbhub
| Driver: usbhub.sys, 3/24/2011 21:29:26, 343040 bytes
| Driver: usbd.sys, 3/24/2011 21:28:59, 7936 bytes

----------------
Gameport Devices
----------------

------------
PS/2 Devices
------------
+ Standard PS/2 Keyboard
| Matching Device ID: *pnp0303
| Service: i8042prt
| Driver: i8042prt.sys, 7/13/2009 17:19:57, 105472 bytes
| Driver: kbdclass.sys, 7/13/2009 19:48:04, 50768 bytes
| 
+ HID Keyboard Device
| Vendor/Product ID: 0x045E, 0x0745
| Matching Device ID: hid_device_system_keyboard
| Service: kbdhid
| Driver: kbdhid.sys, 11/20/2010 21:23:47, 33280 bytes
| Driver: kbdclass.sys, 7/13/2009 19:48:04, 50768 bytes
| 
+ Terminal Server Keyboard Driver
| Matching Device ID: root\rdp_kbd
| Upper Filters: kbdclass
| Service: TermDD
| Driver: i8042prt.sys, 7/13/2009 17:19:57, 105472 bytes
| Driver: kbdclass.sys, 7/13/2009 19:48:04, 50768 bytes
| 
+ Synaptics PS/2 Port TouchPad
| Matching Device ID: *tos0220
| Upper Filters: SynTP
| Service: i8042prt
| 
+ Microsoft USB Dual Receiver Wireless Mouse (IntelliPoint)
| Vendor/Product ID: 0x045E, 0x0745
| Matching Device ID: hid\vid_045e&pid_0745&mi_01&col01
| Upper Filters: Point64
| Service: mouhid
| Driver: point64.sys, 8/1/2011 14:59:06, 45416 bytes
| Driver: mouhid.sys, 7/13/2009 18:00:20, 31232 bytes
| Driver: mouclass.sys, 7/13/2009 19:48:27, 49216 bytes
| Driver: wdfcoinstaller01009.dll, 8/7/2009 12:49:36, 1721576 bytes
| 
+ Terminal Server Mouse Driver
| Matching Device ID: root\rdp_mou
| Upper Filters: mouclass
| Service: TermDD
| Driver: termdd.sys, 11/20/2010 21:23:47, 63360 bytes
| Driver: sermouse.sys, 7/13/2009 18:00:20, 26624 bytes
| Driver: mouclass.sys, 7/13/2009 19:48:27, 49216 bytes

------------------------
Disk & DVD/CD-ROM Drives
------------------------
      Drive: C:
 Free Space: 9.0 GB
Total Space: 460.3 GB
File System: NTFS
      Model: TOSHIBA MK5075GSX ATA Device

      Drive: D:
      Model: TSSTcorp CDDVDW SN-208AB ATA Device
     Driver: c:\windows\system32\drivers\cdrom.sys, 6.01.7601.17514 (English), 11/20/2010 21:23:47, 147456 bytes

      Drive: E:
      Model: MagicISO Virtual DVD-ROM0000
     Driver: c:\windows\system32\drivers\cdrom.sys, 6.01.7601.17514 (English), 11/20/2010 21:23:47, 147456 bytes

--------------
System Devices
--------------
     Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1702&SUBSYS_00000000&REV_00\3&11583659&1&C2
   Driver: n/a

     Name: PCI standard ISA bridge
Device ID: PCI\VEN_1002&DEV_439D&SUBSYS_FD7B1179&REV_40\3&11583659&1&A3
   Driver: C:\windows\system32\DRIVERS\msisadrv.sys, 6.01.7600.16385 (English), 7/13/2009 19:48:27, 15424 bytes

     Name: Standard AHCI 1.0 Serial ATA Controller
Device ID: PCI\VEN_1002&DEV_4391&SUBSYS_FD7B1179&REV_40\3&11583659&1&88
   Driver: C:\windows\system32\DRIVERS\msahci.sys, 6.01.7601.17514 (English), 11/20/2010 21:23:47, 31104 bytes
   Driver: C:\windows\system32\DRIVERS\pciidex.sys, 6.01.7600.16385 (English), 7/13/2009 19:45:46, 48720 bytes
   Driver: C:\windows\system32\DRIVERS\atapi.sys, 6.01.7600.16385 (English), 7/13/2009 19:52:21, 24128 bytes
   Driver: C:\windows\system32\DRIVERS\ataport.sys, 6.01.7601.17514 (English), 11/20/2010 21:23:47, 155520 bytes

     Name: Realtek RTL8188CE Wireless LAN 802.11n PCI-E NIC
Device ID: PCI\VEN_10EC&DEV_8176&SUBSYS_818110EC&REV_01\4&27A8E2B5&0&00A9
   Driver: C:\windows\system32\DRIVERS\rtl8192Ce.sys, 1005.15.0223.2011 (English), 2/23/2011 19:14:44, 1142376 bytes
   Driver: C:\windows\system32\drivers\vwifibus.sys, 6.01.7600.16385 (English), 7/13/2009 18:07:21, 24576 bytes

     Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1701&SUBSYS_00000000&REV_00\3&11583659&1&C1
   Driver: n/a

     Name: Standard Dual Channel PCI IDE Controller
Device ID: PCI\VEN_1002&DEV_439C&SUBSYS_FD7B1179&REV_40\3&11583659&1&A1
   Driver: C:\windows\system32\DRIVERS\pciide.sys, 6.01.7600.16385 (English), 7/13/2009 19:45:45, 12352 bytes
   Driver: C:\windows\system32\DRIVERS\pciidex.sys, 6.01.7600.16385 (English), 7/13/2009 19:45:46, 48720 bytes
   Driver: C:\windows\system32\DRIVERS\atapi.sys, 6.01.7600.16385 (English), 7/13/2009 19:52:21, 24128 bytes
   Driver: C:\windows\system32\DRIVERS\ataport.sys, 6.01.7601.17514 (English), 11/20/2010 21:23:47, 155520 bytes

     Name: ATI I/O Communications Processor SMBus Controller
Device ID: PCI\VEN_1002&DEV_4385&SUBSYS_FD7B1179&REV_42\3&11583659&1&A0
   Driver: n/a

     Name: Realtek PCIe FE Family Controller
Device ID: PCI\VEN_10EC&DEV_8136&SUBSYS_FD7B1179&REV_05\4&1E17DAB7&0&00AA
   Driver: n/a

     Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1700&SUBSYS_00000000&REV_43\3&11583659&1&C0
   Driver: n/a

     Name: Standard OpenHCD USB Host Controller
Device ID: PCI\VEN_1002&DEV_4397&SUBSYS_FD7B1179&REV_00\3&11583659&1&B0
   Driver: C:\windows\system32\drivers\usbohci.sys, 6.01.7601.17586 (English), 3/24/2011 21:29:04, 25600 bytes
   Driver: C:\windows\system32\drivers\usbport.sys, 6.01.7601.17586 (English), 3/24/2011 21:29:14, 325120 bytes
   Driver: C:\windows\system32\drivers\usbhub.sys, 6.01.7601.17586 (English), 3/24/2011 21:29:26, 343040 bytes

     Name: ATI I/O Communications Processor PCI Bus Controller
Device ID: PCI\VEN_1002&DEV_4384&SUBSYS_00000000&REV_40\3&11583659&1&A4
   Driver: C:\windows\system32\DRIVERS\pci.sys, 6.01.7601.17514 (English), 11/20/2010 21:23:47, 184704 bytes

     Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1719&SUBSYS_00000000&REV_00\3&11583659&1&C7
   Driver: n/a

     Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1510&SUBSYS_FD7B1179&REV_00\3&11583659&1&00
   Driver: n/a

     Name: Standard OpenHCD USB Host Controller
Device ID: PCI\VEN_1002&DEV_4397&SUBSYS_FD7B1179&REV_00\3&11583659&1&98
   Driver: C:\windows\system32\drivers\usbohci.sys, 6.01.7601.17586 (English), 3/24/2011 21:29:04, 25600 bytes
   Driver: C:\windows\system32\drivers\usbport.sys, 6.01.7601.17586 (English), 3/24/2011 21:29:14, 325120 bytes
   Driver: C:\windows\system32\drivers\usbhub.sys, 6.01.7601.17586 (English), 3/24/2011 21:29:26, 343040 bytes

     Name: High Definition Audio Controller
Device ID: PCI\VEN_1002&DEV_4383&SUBSYS_FD781179&REV_40\3&11583659&1&A2
   Driver: C:\windows\system32\DRIVERS\hdaudbus.sys, 6.01.7601.17514 (English), 11/20/2010 21:23:47, 122368 bytes

     Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1718&SUBSYS_00000000&REV_00\3&11583659&1&C5
   Driver: n/a

     Name: AMD Radeon HD 6310 Graphics         
Device ID: PCI\VEN_1002&DEV_9802&SUBSYS_FD741179&REV_00\3&11583659&1&08
   Driver: C:\windows\system32\DRIVERS\atikmdag.sys, 8.01.0001.1162 (English), 6/8/2011 00:42:26, 9360896 bytes
   Driver: C:\windows\system32\DRIVERS\ati2erec.dll, 1.00.0000.0020 (English), 6/7/2011 23:14:22, 53248 bytes
   Driver: C:\windows\system32\DRIVERS\atikmpag.sys, 8.14.0001.6214 (English), 6/7/2011 23:16:14, 309760 bytes
   Driver: C:\windows\system32\atiumd64.dll, 7.14.0010.0841 (English), 6/7/2011 23:23:52, 5486592 bytes
   Driver: C:\windows\system32\atiumd6a.dll, 8.14.0010.0312 (English), 6/7/2011 23:36:08, 3810816 bytes
   Driver: C:\windows\system32\atitmm64.dll, 6.14.0011.0023 (English), 6/7/2011 23:53:44, 120320 bytes
   Driver: C:\windows\system32\atiicdxx.dat, 4/20/2011 14:30:08, 233765 bytes
   Driver: C:\windows\system32\amdpcom64.dll, 8.14.0010.0023 (English), 6/7/2011 23:13:16, 53760 bytes
   Driver: C:\windows\system32\atimpc64.dll, 8.14.0010.0023 (English), 6/7/2011 23:13:16, 53760 bytes
   Driver: C:\windows\system32\atiadlxx.dll, 6.14.0010.1061 (English), 6/7/2011 23:17:08, 366592 bytes
   Driver: C:\windows\system32\atiumd6a.cap, 6/7/2011 23:31:44, 1127552 bytes
   Driver: C:\windows\system32\atimuixx.dll, 6.14.0010.1002 (English), 6/7/2011 23:53:00, 16384 bytes
   Driver: C:\windows\system32\atiapfxx.exe, 6.14.0010.1001 (English), 6/7/2011 23:59:42, 151552 bytes
   Driver: C:\windows\system32\atiapfxx.blb, 6/8/2011 00:00:18, 166704 bytes
   Driver: C:\windows\system32\atiumd6v.dll, 7.14.0010.0184 (English), 6/7/2011 23:36:44, 1113088 bytes
   Driver: C:\windows\system32\atiesrxx.exe, 6.14.0011.1096 (English), 6/7/2011 23:54:56, 204288 bytes
   Driver: C:\windows\system32\atieclxx.exe, 6.14.0011.1096 (English), 6/7/2011 23:55:32, 485376 bytes
   Driver: C:\windows\system32\atipdl64.dll, 6.14.0010.2563 (English), 6/7/2011 23:53:24, 423424 bytes
   Driver: C:\windows\system32\atiedu64.dll, 6.14.0010.2514 (English), 6/7/2011 23:52:56, 59392 bytes
   Driver: C:\windows\system32\ATIDEMGX.dll, 2.00.4175.37671 (English), 6/7/2011 23:55:44, 462848 bytes
   Driver: C:\windows\system32\atio6axx.dll, 6.14.0010.10834 (English), 6/8/2011 00:27:16, 23336960 bytes
   Driver: C:\windows\system32\aticaldd64.dll, 6.14.0010.1417 (English), 6/7/2011 23:35:32, 8489472 bytes
   Driver: C:\windows\system32\aticalrt64.dll, 6.14.0010.1417 (English), 6/7/2011 23:35:54, 51200 bytes
   Driver: C:\windows\system32\aticalcl64.dll, 6.14.0010.1417 (English), 6/7/2011 23:35:44, 44544 bytes
   Driver: C:\windows\system32\atipblag.dat, 3/17/2011 15:51:46, 3929 bytes
   Driver: C:\windows\system32\atiu9p64.dll, 8.14.0001.6214 (English), 6/7/2011 23:15:14, 38912 bytes
   Driver: C:\windows\system32\atiuxp64.dll, 8.14.0001.6214 (English), 6/7/2011 23:15:26, 40960 bytes
   Driver: C:\windows\system32\atig6pxx.dll, 8.14.0001.6214 (English), 6/7/2011 23:16:34, 14848 bytes
   Driver: C:\windows\system32\atig6txx.dll, 8.14.0001.6214 (English), 6/7/2011 23:16:28, 39936 bytes
   Driver: C:\windows\system32\atibtmon.exe, 2.00.0000.0000 (English), 5/11/2009 19:35:30, 118784 bytes
   Driver: C:\windows\system32\atidxx64.dll, 8.17.0010.0362 (English), 6/7/2011 23:40:30, 5008384 bytes
   Driver: C:\windows\SysWOW64\atiumdag.dll, 7.14.0010.0841 (English), 6/7/2011 23:30:00, 4330496 bytes
   Driver: C:\windows\SysWOW64\atiumdva.dll, 8.14.0010.0312 (English), 6/7/2011 23:27:02, 4017152 bytes
   Driver: C:\windows\SysWOW64\amdpcom32.dll, 8.14.0010.0023 (English), 6/7/2011 23:13:02, 52736 bytes
   Driver: C:\windows\SysWOW64\atimpc32.dll, 8.14.0010.0023 (English), 6/7/2011 23:13:02, 52736 bytes
   Driver: C:\windows\SysWOW64\atiadlxy.dll, 6.14.0010.1061 (English), 6/7/2011 23:16:56, 262144 bytes
   Driver: C:\windows\SysWOW64\atiumdva.cap, 6/7/2011 23:26:14, 1127552 bytes
   Driver: C:\windows\SysWOW64\atiumdmv.dll, 7.14.0010.0184 (English), 6/7/2011 23:36:20, 1828864 bytes
   Driver: C:\windows\SysWOW64\atipdlxx.dll, 6.14.0010.2563 (English), 6/7/2011 23:53:18, 356352 bytes
   Driver: C:\windows\SysWOW64\Oemdspif.dll, 6.15.0006.0006 (English), 6/7/2011 23:53:06, 278528 bytes
   Driver: C:\windows\SysWOW64\ati2edxx.dll, 6.14.0010.2514 (English), 6/7/2011 23:52:50, 43520 bytes
   Driver: C:\windows\SysWOW64\atioglxx.dll, 6.14.0010.10834 (English), 6/8/2011 00:05:34, 17940992 bytes
   Driver: C:\windows\SysWOW64\atidxx32.dll, 8.17.0010.0362 (English), 6/7/2011 23:49:34, 4219904 bytes
   Driver: C:\windows\SysWOW64\aticaldd.dll, 6.14.0010.1417 (English), 6/7/2011 23:32:02, 6847488 bytes
   Driver: C:\windows\SysWOW64\aticalrt.dll, 6.14.0010.1417 (English), 6/7/2011 23:35:52, 46080 bytes
   Driver: C:\windows\SysWOW64\aticalcl.dll, 6.14.0010.1417 (English), 6/7/2011 23:35:42, 44032 bytes
   Driver: C:\windows\SysWOW64\atipblag.dat, 3/17/2011 15:51:46, 3929 bytes
   Driver: C:\windows\SysWOW64\atiu9pag.dll, 8.14.0001.6214 (English), 6/7/2011 23:15:06, 29184 bytes
   Driver: C:\windows\SysWOW64\atiuxpag.dll, 8.14.0001.6214 (English), 6/7/2011 23:15:20, 31744 bytes
   Driver: C:\windows\SysWOW64\atigktxx.dll, 8.14.0001.6214 (English), 6/7/2011 23:16:20, 32768 bytes
   Driver: C:\windows\SysWOW64\atiglpxx.dll, 8.14.0001.6214 (English), 6/7/2011 23:16:30, 12800 bytes
   Driver: C:\windows\atiogl.xml, 5/19/2011 06:13:40, 32635 bytes
   Driver: C:\windows\system32\ATIODCLI.exe, 1.00.0000.0001 (English), 6/22/2009 13:34:36, 51200 bytes
   Driver: C:\windows\system32\ATIODE.exe, 1.00.0000.0001 (English), 8/27/2010 16:33:08, 332800 bytes
   Driver: C:\windows\system32\atiglpxx.dll, 8.14.0001.6214 (English), 6/7/2011 23:16:30, 12800 bytes
   Driver: C:\windows\system32\aticfx64.dll, 8.17.0010.1083 (English), 6/7/2011 23:58:16, 811008 bytes
   Driver: C:\windows\SysWOW64\aticfx32.dll, 8.17.0010.1083 (English), 6/7/2011 23:59:28, 688128 bytes
   Driver: C:\windows\system32\coinst.dll, 1.00.0003.0005 (English), 6/7/2011 23:25:54, 58880 bytes

     Name: Standard OpenHCD USB Host Controller
Device ID: PCI\VEN_1002&DEV_4397&SUBSYS_FD7B1179&REV_00\3&11583659&1&90
   Driver: C:\windows\system32\drivers\usbohci.sys, 6.01.7601.17586 (English), 3/24/2011 21:29:04, 25600 bytes
   Driver: C:\windows\system32\drivers\usbport.sys, 6.01.7601.17586 (English), 3/24/2011 21:29:14, 325120 bytes
   Driver: C:\windows\system32\drivers\usbhub.sys, 6.01.7601.17586 (English), 3/24/2011 21:29:26, 343040 bytes

     Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1716&SUBSYS_00000000&REV_00\3&11583659&1&C6
   Driver: n/a

     Name: PCI standard PCI-to-PCI bridge
Device ID: PCI\VEN_1002&DEV_43A2&SUBSYS_00001002&REV_00\3&11583659&1&AA
   Driver: C:\windows\system32\DRIVERS\pci.sys, 6.01.7601.17514 (English), 11/20/2010 21:23:47, 184704 bytes

     Name: Standard Enhanced PCI to USB Host Controller
Device ID: PCI\VEN_1002&DEV_4396&SUBSYS_FD7B1179&REV_00\3&11583659&1&B2
   Driver: C:\windows\system32\drivers\usbehci.sys, 6.01.7601.17586 (English), 3/24/2011 21:29:04, 52736 bytes
   Driver: C:\windows\system32\drivers\usbport.sys, 6.01.7601.17586 (English), 3/24/2011 21:29:14, 325120 bytes
   Driver: C:\windows\system32\drivers\usbhub.sys, 6.01.7601.17586 (English), 3/24/2011 21:29:26, 343040 bytes

     Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1704&SUBSYS_00000000&REV_00\3&11583659&1&C4
   Driver: n/a

     Name: PCI standard PCI-to-PCI bridge
Device ID: PCI\VEN_1002&DEV_43A1&SUBSYS_00001002&REV_00\3&11583659&1&A9
   Driver: C:\windows\system32\DRIVERS\pci.sys, 6.01.7601.17514 (English), 11/20/2010 21:23:47, 184704 bytes

     Name: Standard Enhanced PCI to USB Host Controller
Device ID: PCI\VEN_1002&DEV_4396&SUBSYS_FD7B1179&REV_00\3&11583659&1&9A
   Driver: C:\windows\system32\drivers\usbehci.sys, 6.01.7601.17586 (English), 3/24/2011 21:29:04, 52736 bytes
   Driver: C:\windows\system32\drivers\usbport.sys, 6.01.7601.17586 (English), 3/24/2011 21:29:14, 325120 bytes
   Driver: C:\windows\system32\drivers\usbhub.sys, 6.01.7601.17586 (English), 3/24/2011 21:29:26, 343040 bytes

     Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1703&SUBSYS_00000000&REV_00\3&11583659&1&C3
   Driver: n/a

     Name: PCI standard PCI-to-PCI bridge
Device ID: PCI\VEN_1002&DEV_43A0&SUBSYS_00001002&REV_00\3&11583659&1&A8
   Driver: C:\windows\system32\DRIVERS\pci.sys, 6.01.7601.17514 (English), 11/20/2010 21:23:47, 184704 bytes

     Name: Standard Enhanced PCI to USB Host Controller
Device ID: PCI\VEN_1002&DEV_4396&SUBSYS_FD7B1179&REV_00\3&11583659&1&92
   Driver: C:\windows\system32\drivers\usbehci.sys, 6.01.7601.17586 (English), 3/24/2011 21:29:04, 52736 bytes
   Driver: C:\windows\system32\drivers\usbport.sys, 6.01.7601.17586 (English), 3/24/2011 21:29:14, 325120 bytes
   Driver: C:\windows\system32\drivers\usbhub.sys, 6.01.7601.17586 (English), 3/24/2011 21:29:26, 343040 bytes

---------------
EVR Power Information
---------------
Current Setting: {5C67A112-A4C9-483F-B4A7-1D473BECAFDC} (Quality) 
  Quality Flags: 2576
    Enabled:
    Force throttling
    Allow half deinterlace
    Allow scaling
    Decode Power Usage: 100
  Balanced Flags: 1424
    Enabled:
    Force throttling
    Allow batching
    Force half deinterlace
    Force scaling
    Decode Power Usage: 50
  PowerFlags: 1424
    Enabled:
    Force throttling
    Allow batching
    Force half deinterlace
    Force scaling
    Decode Power Usage: 0

```

I did it really fast so Sound part of DxDiag didnt actually load right >_<

---

