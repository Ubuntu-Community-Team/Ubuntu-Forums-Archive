---
title: "Installation step failed"
date: 2007-08-01
forum: General Help
---

### Post by iNeedHelp3 on 2007-08-01
After running wubi and rebooting, everything looks to be going great until I get the message "Installation step failed -> Load installer components from CD"
after this message I get back in the "Ubuntu installer main menu" and there I again select "Load installer components from CD" then I get in a new menu where I can select "Load Iso: Load installer components from installer iso"
after this I again get the message "Installation step failed -> Load installer components from CD", and then return to the "Ubuntu installer main menu" where I get 2 more options "Scan HD for Iso" & "load installer components from iso".
the "scan HD for Iso" returns an error when i don't copy an extra alternate iso in the root of my c: drive, but even with this copy I still keep returning to the "Installation step failed -> Load installer components from CD" error.
I'm running Win2k, and I really need help to get this working.

---

### Post by YouMustFirstRegister on 2007-08-01
I had the same problem 

WinXP home
2.41Ghz
512MB RAM
180 GB HD, 80 used 100 free, FAT32

This is what I did 

Downloaded and installed Wubi on another PC, which downloaded the Ubuntu ISO as it installed
Started doing the same on this one
Realised I already had the ISO on the other PC and didn't want to download it again
Copied the install directory from the other PC to this one
Ran the Wubi installer on this PC
It didn't download any more ISO as it was already there. it just rebooted and started to install
During install it gave the error mentioned


I checked the sizes of the ISO on this and the other PC. They're both the same

So then I rebooted and trashed ubuntu-7.04-alternate-i386.iso.partial as that was from when I first started downloading, before I copied ubuntu-7.04-alternate-i386.iso from the other PC. 
Rebooted and tried the install again
Got something like "cannot use alternate ISO image, rebooting in 10 secs"

Now I've unistalled it and am reinstalling from scratch and allowing it to download the ISO from the location it wants to

---

### Post by ago on 2007-08-02
Do a clean installation again, if that happens hit Alt+F4 and see if there is any relevant error. To look at older error hit Alt+F2 and then run "nano /var/log/syslog"

---

### Post by Manav Kataria on 2008-01-05
Hi Ago,

I am facing a similar problem: 
[B]1. "Installation step failed -> Load installer components from CD" and
2. "Failed to find an installer iso image"
[/B]
> **ago said:**
> Do a clean installation again, if that happens hit Alt+F4 and see if there is any relevant error. To look at older error hit Alt+F2 and then run "nano /var/log/syslog"

This is what I gathered from syslog: 

> 1197 Jan  5 19:01:37 kernel: [   26.768000] XFS: bad magic number
1198 Jan  5 19:01:37 kernel: [   26.768000] XFS: SB validate failed
1199 Jan  5 19:01:37 main-menu[4891]: s/system.virtual.disk 


**Formatting the root device fails** (see line #1289) :
> Jan  5 19:01:37 main-menu[4891]: (process:6003): +  
Jan  5 19:01:37 main-menu[4891]: (process:6003): mkfs.ext3 
Jan  5 19:01:37 main-menu[4891]: (process:6003):  -v 
Jan  5 19:01:37 main-menu[4891]: (process:6003):  -F 
Jan  5 19:01:37 main-menu[4891]: (process:6003):   
Jan  5 19:01:37 loop-install: Cannot create file system for /media/host/wubi/disks/system.virtual.disk, giving up
Jan  5 19:01:37 main-menu[4891]: /media/host/wubi/disks/system.virtual.disk 
Jan  5 19:01:37 main-menu[4891]: (process:6003):  
Jan  5 19:01:37 main-menu[4891]: (process:6003): mke2fs 1.40-WIP (14-Nov-2006) 
Jan  5 19:01:37 main-menu[4891]: (process:6003): mkfs.ext3 
Jan  5 19:01:37 main-menu[4891]: (process:6003): :  
Jan  5 19:01:37 main-menu[4891]: (process:6003):[B] Device size reported to be zero.  Invalid partition specified, or 
Jan  5 19:01:37 main-menu[4891]: (process:6003): ^Ipartition table wasn't reread after running fdisk, due to 
Jan  5 19:01:37 main-menu[4891]: (process:6003): ^Ia modified partition being busy and in use.  You may need to reboot 
Jan  5 19:01:37 main-menu[4891]: (process:6003): ^Ito re-read your partition table. 
Jan  5 19:01:37 main-menu[4891]: (process:6003): ^M [/B]
Jan  5 19:01:37 main-menu[4891]: (process:6003): +  
Jan  5 19:01:37 main-menu[4891]: (process:6003): log 
Jan  5 19:01:37 main-menu[4891]: (process:6003):  Cannot create file system for /media/host/wubi/disks/system.virtual.disk, giving up 
Jan  5 19:01:37 main-menu[4891]: (process:6003):  
Jan  5 19:01:37 main-menu[4891]: (process:6003): +  
Jan  5 19:01:37 main-menu[4891]: (process:6003): logger 
Jan  5 19:01:37 main-menu[4891]: (process:6003):  -t 
Jan  5 19:01:37 main-menu[4891]: (process:6003):  loop-install 
Jan  5 19:01:37 main-menu[4891]: (process:6003):  Cannot create file system for /media/host/wubi/disks/system.virtual.disk, giving up 
Jan  5 19:01:37 main-menu[4891]: (process:6003):  
Jan  5 19:01:37 main-menu[4891]: (process:6003): +  
Jan  5 19:01:37 main-menu[4891]: (process:6003): return 
Jan  5 19:01:37 main-menu[4891]: (process:6003):  1 
Jan  5 19:01:37 main-menu[4891]: (process:6003):  
Jan  5 19:01:37 main-menu[4891]: (process:6003): +  
Jan  5 19:01:37 main-menu[4891]: (process:6003): log 
Jan  5 19:01:37 main-menu[4891]: (process:6003):  Unable to mount loop device 
Jan  5 19:01:37 main-menu[4891]: (process:6003):  
Jan  5 19:01:37 main-menu[4891]: (process:6003): + 
Jan  5 19:01:37 loop-install: Unable to mount loop device
Jan  5 19:01:37 main-menu[4891]:   
Jan  5 19:01:37 main-menu[4891]: (process:6003): logger 
Jan  5 19:01:37 main-menu[4891]: (process:6003):  -t 
Jan  5 19:01:37 main-menu[4891]: (process:6003):  loop-install 
Jan  5 19:01:37 main-menu[4891]: (process:6003):  Unable to mount loop device 
Jan  5 19:01:37 main-menu[4891]: (process:6003):  
Jan  5 19:01:37 main-menu[4891]: (process:6003): +  
Jan  5 19:01:37 main-menu[4891]: (process:6003): return 
Jan  5 19:01:37 main-menu[4891]: (process:6003):  1 
Jan  5 19:01:37 main-menu[4891]: (process:6003):  
Jan  5 19:01:37 main-menu[4891]: WARNING **: Configuring 'load-cdrom' failed with error code 1 
Jan  5 19:01:37 main-menu[4891]: WARNING **: Menu item 'load-cdrom' failed. 
Jan  5 19:05:36 main-menu[4891]: INFO: Modifying debconf priority limit from 'critical' to 'medium' 
Jan  5 19:05:36 debconf: Setting debconf/priority to medium
Jan  5 19:05:37 main-menu[4891]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored) 
Jan  5 19:05:37 main-menu[4891]: DEBUG: resolver (ext2-modules): package doesn't exist (ignored) 
Jan  5 19:05:37 main-menu[4891]: DEBUG: resolver (user-setup): package doesn't exist (ignored) 
Jan  5 19:05:37 main-menu[4891]: DEBUG: resolver (firmware-modules): package doesn't exist (ignored) 
Jan  5 19:05:37 main-menu[4891]: INFO: Falling back to the package description for console-setup-udeb 
Jan  5 19:05:37 anna-install: Installing ext2-modules
Jan  5 19:05:37 os-prober: unknown udeb ext2-modules
Jan  5 19:05:37 anna-install: Installing ext3-modules


I am not sure why does wubi suspect a problem with my partition table. I tried this installation several times from scratch, but I see this error every time. 
I have successfully installed ubuntu before frm the same ISO. 7.04 alternate on a different machine and it worked like a charm! The problem may be specific to this laptop. Do let me know if you need further information. 

Secondly, I suspect wubi uninstall isn't cleaning up properly. It prompts me to run **MS fdisk** on every *clean *reinstall attempt. I'll try running a **MS fdisk** and retry the installation. And post my updates, if any. 

Please find syslog (.zip) attached. 


Thanks a ton!
Manav

---

### Post by Manav Kataria on 2008-01-05
> **Manav Kataria said:**
> 
Secondly, I suspect wubi uninstall isn't cleaning up properly. It prompts me to run **MS fdisk** on every *clean *reinstall attempt. I'll try running a **MS fdisk** and retry the installation. And post my updates, if any. 


OK. Tell me something: 
    1. Do I *really *need to run a *MS fdisk *on *MBR*? 
    2. Is it possible to run fdisk on MBR from /windows XP/ or do I /need/ to create a boot disk! <-- Coz that's a pain! :(

Thanks,
-Manav

---

### Post by ago on 2008-01-07
The issue seems to be that system.virtual.disk is of size zero when it should be a few GB.
There was a bug in 7.04 that was fixed in 7.10.

It is also possible to generate a file of the appropriate size with any other tool and replace system.virtual.disk.

---

### Post by Manav Kataria on 2008-01-10
> **ago said:**
> The issue seems to be that system.virtual.disk isof size zero when it should be a few GB.
There was a bug in 7.04 that was fixed in 7.10.


Thanks Ago!

I tried the 7.10 version as well. But it hangs post reboot when attempting to start Ubiquity: X starts but doesn't throw any icon/message on the screen. The mouse (pointer) does respond though.

I had some difficulty getting my hands on the log: 
+ Alt+F{1,2,3..} doesn't yield a new terminal. 
+ Killing Ubiquity throws the main terminal, but almost immediately attempts a restart thus throwing back the X. This short time is insufficient to copy /var/log/syslog to an (un?)mounted windows partition. The new X session is the same (no icons/message just the mouse pointer with the wallpaper) as the first one. That is, no way to proceed with installation. 

Please suggest how to retrieve the logs in 7.10 wubi. Nevertheless that would be a different bug. 

> **ago said:**
> 
It is also possible to generate a file of the appropriate size with any other tool and replace system.virtual.disk.

So this is what I'll try next with 7.04 (please let me know if I am missing something):
1. Create an EXT2 file system image called system.virtual.disk in the wubi directory, from the command line. 
2. Reboot and continue with Wubi Ubuntu Installation? 

Thanks
Manav

---

### Post by ago on 2008-01-10
> **Manav Kataria said:**
> 
I tried the 7.10 version as well. But it hangs post reboot when attempting to start Ubiquity: X starts but doesn't throw any icon/message on the screen. The mouse (pointer) does respond though.
That's a different issue 

> I had some difficulty getting my hands on the log: 
+ Alt+F{1,2,3..} doesn't yield a new terminal.
Ctrl + alt + f2

---

### Post by Manav Kataria on 2008-01-11
> **ago said:**
> That's a different issue 

Could you please point me to its resolution. If it has one.

Thank you,
Manav

---

### Post by ago on 2008-01-11
It looks like an X problem mostly. You should get to a console first vit ctrl+alt+f1 and debug from there by looking at the logs. An easier way might be to press esc at the countdown and select safe graphic mode.

---

### Post by Manav Kataria on 2008-01-14
Ago, 

> **ago said:**
> It looks like an X problem mostly. You should get to a console first vit ctrl+alt+f1 and debug from there by looking at the logs. An easier way might be to press esc at the countdown and select safe graphic mode.

While installing 7.10 the major issue I think is :
--------------------------------
> Jan 14 19:41:33 ubuntu firmware_helper[8940]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:04.0' with driver 'bcm43xx'
Jan 14 19:41:33 ubuntu kernel: [  511.524000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Jan 14 19:41:33 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): could not trigger wireless scan on device eth1: No such device 


Also, just a sidenote. The systems performance goes ***extremely*** low during this point. So much that each ls could takes around 5-20+ seconds to execute. Copying syslog (~70KB) to a mounted partition took more than a minute, when it should typically be fraction of seconds! 

I monitored the *top* result for a while. And I could only see ubiquity taking b/w 0.3 to 3% of CPU, and 6% of memory. xorg taking upto 1.5% CPU. which seems a bit irrational - no processes taking full cpu, yet the response time being so bad?!

Hope this helps anyone who's testing/debugging 7.10 wubi.

Regards,
Manav

PS: 
syslog snippet (line#633 onwards) from 7.10 installation attempt: 
--------------------------------
> Jan 15 01:04:04 ubuntu kernel: [   66.192000] [drm] Initialized drm 1.1.0 20060810
Jan 15 01:04:04 ubuntu kernel: [   66.208000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 21
Jan 15 01:04:04 ubuntu kernel: [   66.208000] [drm] Initialized i915 1.6.0 20060119 on minor 0
Jan 14 19:34:10 ubuntu ntpdate[8819]: step time server 91.189.94.4 offset -19799.836171 sec
Jan 14 19:34:12 ubuntu kernel: [   74.224000] eth0: no IPv6 routers present
Jan 14 19:34:34 ubuntu firmware_helper[8834]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:04.0' with driver 'bcm43xx'
Jan 14 19:34:34 ubuntu kernel: [   96.208000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Jan 14 19:34:36 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): could not trigger wireless scan on device eth1: No such device 
Jan 14 19:34:59 ubuntu firmware_helper[8845]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:04.0' with driver 'bcm43xx'
Jan 14 19:34:59 ubuntu kernel: [  121.068000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Jan 14 19:35:01 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): could not trigger wireless scan on device eth1: No such device 
Jan 14 19:35:25 ubuntu firmware_helper[8851]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:04.0' with driver 'bcm43xx'
Jan 14 19:35:25 ubuntu kernel: [  147.280000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Jan 14 19:35:26 ubuntu ubiquity[8832]: Ubiquity 1.6.8
Jan 14 19:35:27 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): could not trigger wireless scan on device eth1: No such device 
Jan 14 19:35:48 ubuntu firmware_helper[8868]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:04.0' with driver 'bcm43xx'
Jan 14 19:35:48 ubuntu kernel: [  170.252000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Jan 14 19:35:50 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): could not trigger wireless scan on device eth1: No such device 
Jan 14 19:36:11 ubuntu firmware_helper[8873]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:04.0' with driver 'bcm43xx'
Jan 14 19:36:11 ubuntu kernel: [  193.664000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Jan 14 19:36:13 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): could not trigger wireless scan on device eth1: No such device 
Jan 14 19:36:38 ubuntu firmware_helper[8885]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:04.0' with driver 'bcm43xx'
Jan 14 19:36:38 ubuntu kernel: [  220.580000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Jan 14 19:36:40 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): could not trigger wireless scan on device eth1: No such device 
Jan 14 19:37:00 ubuntu firmware_helper[8892]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:04.0' with driver 'bcm43xx'
Jan 14 19:37:00 ubuntu kernel: [  242.776000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Jan 14 19:37:02 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): could not trigger wireless scan on device eth1: No such device 
Jan 14 19:38:23 ubuntu ubiquity[8832]: log-output -t ubiquity laptop-detect
Jan 14 19:39:21 ubuntu kernel: [  383.048000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Jan 14 19:39:23 ubuntu firmware_helper[8927]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:04.0' with driver 'bcm43xx'
Jan 14 19:39:25 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): could not trigger wireless scan on device eth1: No such device 
Jan 14 19:41:33 ubuntu firmware_helper[8940]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:04.0' with driver 'bcm43xx'
Jan 14 19:41:33 ubuntu kernel: [  511.524000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Jan 14 19:41:33 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): could not trigger wireless scan on device eth1: No such device 
Jan 14 19:43:53 ubuntu firmware_helper[8971]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:04.0' with driver 'bcm43xx'
Jan 14 19:43:54 ubuntu kernel: [  654.928000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Jan 14 19:44:01 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): could not trigger wireless scan on device eth1: No such device 
Jan 14 19:44:48 ubuntu kernel: [  710.092000] usb 2-2: USB disconnect, address 3
Jan 14 19:45:00 ubuntu hcid[8669]: HCI dev 0 down
Jan 14 19:45:16 ubuntu NetworkManager: <debug> [1200339911.907885] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_11d_noserial_if0_bluetooth_hci'). 
Jan 14 19:45:16 ubuntu hcid[8669]: Stopping security manager 0
Jan 14 19:45:16 ubuntu hcid[8669]: Device hci0 has been disabled
Jan 14 19:45:16 ubuntu hcid[8669]: HCI dev 0 unregistered
Jan 14 19:45:16 ubuntu hcid[8669]: Unregister path: /org/bluez/hci0
Jan 14 19:45:16 ubuntu hcid[8669]: Device hci0 has been removed
Jan 14 19:45:29 ubuntu NetworkManager: <debug> [1200339929.515713] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_11d_noserial_if1'). 
Jan 14 19:45:34 ubuntu NetworkManager: <debug> [1200339934.851470] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_11d_noserial_if2'). 
Jan 14 19:45:34 ubuntu NetworkManager: <debug> [1200339934.852524] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_11d_noserial_if3'). 
Jan 14 19:45:34 ubuntu NetworkManager: <debug> [1200339934.871188] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_11d_noserial_usbraw'). 
Jan 14 19:45:34 ubuntu NetworkManager: <debug> [1200339934.872257] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_11d_noserial_if0'). 
Jan 14 19:45:34 ubuntu NetworkManager: <debug> [1200339934.873078] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_11d_noserial'). 
Jan 14 19:46:15 ubuntu firmware_helper[8998]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:04.0' with driver 'bcm43xx'
Jan 14 19:46:15 ubuntu kernel: [  796.544000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Jan 14 19:46:21 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): could not trigger wireless scan on device eth1: No such device 


---

### Post by ago on 2008-01-14
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)

for the system responsiveness use system monitor have also a look at hard disk and swap usage. It would be useful if you could find the bottleneck.

---

### Post by Manav Kataria on 2008-02-21
I do not have that system with me since the past few days. I'll give you an update on the _Performance issue_ when I get a chance at it again. 

Thanks,
Manav

---

### Post by ago on 2008-02-21
Can you pls try with wubi 8.04 rev 431 + latest daily ubuntu ISO?

---

