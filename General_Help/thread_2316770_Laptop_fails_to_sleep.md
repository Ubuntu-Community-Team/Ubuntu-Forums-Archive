---
title: "Laptop fails to sleep"
date: 2016-03-10
forum: General Help
---

### Post by Le3eVolfoni on 2016-03-10
I installed ubuntu 14.04 on my mothers's rather old machine and I am facing an odd problem. The computer can't suspend. The screen turns off well but when the PC should suspend, the screen wakes up. Same thing happens when I use "pm-suspend", the screen turns off not even a second, some lines appear on the screen to fast for me to read them, and then the screen turns on.

I checked "acpitool -w" and here is the result

 

      > 1. LANC      S4    *disabled
      2. P32      S0    *disabled  pci:0000:00:1e.0
      3. KBC      S3    *enabled   pnp:00:03
      4. MOUE      S3    *disabled  pnp:00:04
      5. CIR0      S5    *enabled   pnp:00:05
      6. EXP2      S5    *disabled  pci:0000:00:1c.1
      7. PXSX      S5    *enabled   pci:0000:03:00.0
      8. EXP6      S0    *disabled  pci:0000:00:1c.5
      9. PXSX      S0    *disabled




I managed to disable through an upstart script KBC and CIR0, with no luck. PXSX stays enabled despite of the script.

I tried as well to disconnect all the usb devices linked to the computer, nothing changed.

Here is the last entry of the "/var/log/pm-suspend.log" file after I executed the "pm-suspend" command. I tried to understand it but it is above my linux understanding.

    > mercredi 9 mars 2016, 13:37:43 (UTC+0100): performing suspend
    sh: echo: I/O error
    mercredi 9 mars 2016, 13:37:43 (UTC+0100): Awake.
    mercredi 9 mars 2016, 13:37:43 (UTC+0100): Running hooks for resume
    Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
    /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
    
    Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
    /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
    
    Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
    /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
    
    Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
    /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
    
    Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
    
    /dev/sda:
     setting Advanced Power Management level to 0xfe (254)
     APM_level    = 254
    /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
    
    Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
    /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
    
    Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
    /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
    
    Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
    /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
    
    Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
    Reloaded unloaded modules.
    /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
    
    Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
    Selected interface 'wlan0'
    OK
    /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
    
    Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
    /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
    
    Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
    /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
    
    Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
    /etc/pm/sleep.d/10_grub-common resume suspend: success.
    
    Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
    /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
    
    Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
    /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
    
    Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
    /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
    
    Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
    /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
    
    mercredi 9 mars 2016, 13:37:44 (UTC+0100): Finished.

Just in case of I updated my video card drivers as well, cause I had no idea what else to do.

And here is the summary of hardinfo

    > -Computer-
    Processor        : 2x Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz
    Memory        : 4044MB (753MB used)
    Operating System        : Ubuntu 14.04.4 LTS
    User Name        : freddie (Freddie)
    Date/Time        : mer. 09 mars 2016 13:44:09 CET
    -Display-
    Resolution        : 1280x800 pixels
    OpenGL Renderer        : GeForce 9600M GT/PCIe/SSE2
    X11 Vendor        : The X.Org Foundation
    -Multimedia-
    Audio Adapter        : HDA-Intel - HDA Intel
    -Input Devices-
     Power Button
     Lid Switch
     Sleep Button
     Power Button
     AT Translated Set 2 keyboard
     SynPS/2 Synaptics TouchPad
     Video Bus
     ENE eHome Infrared Remote Receiver
     MCE IR Keyboard/Mouse (ene_ir)
     ST LIS3LV02DL Accelerometer
     HDA Intel Dock Mic
     HDA Intel Mic
     HDA Intel Front Headphone
     HDA Intel HDMI/DP,pcm        : 3 Phantom=
     HP WMI hotkeys
     Logitech M315/235/317
     Logitech K230
     HP Webcam
    -Printers-
    No printers found
    -SCSI Disks-
    ATA TOSHIBA MK3252GS
    TSSTcorp CDDVDW TS-L633L
    SanDisk Cruzer Blade

Thanks for any help you could provide, if anything else is needed I'd be happy to provide more infos.

---

### Post by Le3eVolfoni on 2016-03-12
I am running out of ideas and don't know where to look to find the beggining of something. Any idea, anyone ?

---

