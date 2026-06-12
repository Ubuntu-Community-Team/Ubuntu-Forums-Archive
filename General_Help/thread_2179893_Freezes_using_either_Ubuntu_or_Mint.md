---
title: "Freezes using either Ubuntu or Mint"
date: 2013-10-10
forum: General Help
---

### Post by starriol on 2013-10-10
Summary: PC freezes randomly, using it or not, under Debian & Ubuntu latest's versions with KDE, 64 bits. It was working perfectly with Windows 8. What could be the problem???


Full analysis:


1) High CPU temperature causing the issue: Doesn't make sense. The hardware was running perfectly under heavy load in Windows, so with no CPU load in Linux it shouldn’t freeze.
This motherboard's CPU temp sensor is not reliable under Linux, but if I restart as soon as it freezes, the BIOS says the temp is 45 Celsius (113 Fahrenheit). I've run this CPU stable at 70 Celsius, so I don't think it could have dropped more than 20 degrees in the 10 seconds it took me to check out the temp after restarting it.


2) Safeboot/UEFI/CSM (Compatibility Support Module): Secure boot can't be disabled in my motherboard. But I've configured OS Type to "Other OS", which is described as "Get the optimized function when booting on Windows non-UEFI mode, Windows Vista/XP or other Microsoft Secure Boot non-compliant OS.". Also, fastboot is disabled just in case. I'm not really familiar with these technologies, but all the problems regarding them I've seen mentioned at different forums talk about not being able to boot using UEFI/ Safe Boot but nothing is mentioned about the system being unstable.
CSM allows to boot from either UEFI, Legacy OpROM or both. I’ve tested this under Legacy OpROM & both, it freezes anyway.
My motherboard is an Asus Asus M5A99X EVO R2.0 - BIOS revision 1708. It's reported as working perfectly under a whole different range of Linux distros & versions. It’s even said to be working fine at Linux Ubuntu's hardware compatibility site: [http://community.linuxUbuntu.com/hardware/view/15647](http://community.linuxUbuntu.com/hardware/view/15647)


3) Faulty RAM, PSU or SSD: I'm using a Crucial M4. I haven't swapped the RAM, PSU or SSD drive, since I assumed that if they work with Windows, they are working properly. Should I? Did anyone encounter a similar case that was solved by swapping either of these components?


4) IOMMU: I've seen a post reporting that could cause stability issues, [https://bbs.archlinux.org/viewtopic.php?id=163102](https://bbs.archlinux.org/viewtopic.php?id=163102). I don't know if it's enabled or not, I’m not at the PC now, but I’ll check it out later.


5) KDE: I don't know if the particular version of KDE with my particular hardware / BIOS settings could have anything to do, but I'm going to try Ubuntu with Mate to see if it changes anything.


6) AHCI mode: it's enabled, does it makes sense to disable it?


BTW, after this, I'm posting /var/log/messages near the time of the lock-up. I don't see ANY mention to any issues or the freeze itself... but let me know!
If you want to check the whole log from the time Linux booted & the freeze, please see this link: [http://pastebin.com/jkmX4KMg](http://pastebin.com/jkmX4KMg)


Thanks again!!!


Oct  9 22:26:15 Pamela kernel: [    6.471601] r8169 0000:02:00.0: eth0: unable to load firmware patch rtl_nic/rtl8168f-1.fw (-2)
Oct  9 22:26:15 Pamela kernel: [    6.481385] r8169 0000:02:00.0: eth0: link down
Oct  9 22:26:15 Pamela kernel: [    6.481400] r8169 0000:02:00.0: eth0: link down
Oct  9 22:26:15 Pamela kernel: [    6.484976] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  9 22:26:15 Pamela kernel: [    6.595675] lp: driver loaded but no devices found
Oct  9 22:26:15 Pamela kernel: [    6.602739] ppdev: user-space parallel port driver
Oct  9 22:26:17 Pamela kernel: [    8.070241] r8169 0000:02:00.0: eth0: link up
Oct  9 22:26:17 Pamela kernel: [    8.868573] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  9 22:26:17 Pamela kernel: [    8.875061] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct  9 22:26:17 Pamela kernel: [    8.889553] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Oct  9 22:27:37 Pamela org.kde.powerdevil.backlighthelper: QDBusConnection: system D-Bus connection created before QCoreApplication. Application may misbehave.
Oct  9 22:28:12 Pamela kernel: [  123.721254] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
Oct  9 22:49:11 Pamela kernel: [ 1382.569862] fuse init (API version 7.17)
Oct  9 22:49:39 Pamela kernel: [ 1410.849393] device-mapper: uevent: version 1.0.3
Oct  9 22:49:39 Pamela kernel: [ 1410.849566] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]

---

### Post by oldfred on 2013-10-10
What video card? And what version of Ubuntu. I know Intel and nVidia have made a lot of fixes that are now in the kernel & drivers of beta 13.10, have not followed what AMD has done, but I also assume the newest version may be required for the very newest hardware.

Microsoft requires vendors to let users turn off secure boot. Some require a password. While Asus may say allowing CSM is that, you still  should be able to use UEFI. Some systems default to efi partition for UEFI boot files and if not found then look at MBR for BIOS boot files when in CSM mode.

---

### Post by starriol on 2013-10-10
> **oldfred said:**
> What video card? And what version of Ubuntu. I know Intel and nVidia have made a lot of fixes that are now in the kernel & drivers of beta 13.10, have not followed what AMD has done, but I also assume the newest version may be required for the very newest hardware.

Microsoft requires vendors to let users turn off secure boot. Some require a password. While Asus may say allowing CSM is that, you still  should be able to use UEFI. Some systems default to efi partition for UEFI boot files and if not found then look at MBR for BIOS boot files when in CSM mode.

Hi, I'm using an ATI Radeon HD 5750.
Do you think I should be installing something that is not the default drivers?
It's a pretty well supported vard, I would guess.

And I had the exact issue under Debian stable & Ubuntu latest.

---

### Post by oldfred on 2013-10-10
I do not know about AMD enough to really help.

Do you have dual graphics? Like this thread?
 Switchable Graphics is killing my Ubuntu Experience - see post #9 AMD
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)

---

### Post by starriol on 2013-10-11
> **oldfred said:**
> I do not know about AMD enough to really help.

Do you have dual graphics? Like this thread?
 Switchable Graphics is killing my Ubuntu Experience - see post #9 AMD
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)

Nope, just a regular ATI 5770 board :(

---

### Post by oldfred on 2013-10-11
Some links.

 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1)
On the proprietary driver side, the AMD Catalyst 12.11 Beta Linux graphics driver was used. For this initial testing, three discrete graphics cards from the AMD Radeon HD 5000/6000 series were used, since pre-HD5000 graphics cards are now on the Catalyst Legacy driver and the latest-generation Radeon HD 7000 series hardware still doesn't fully work with the open-source Gallium3D "RadeonSI" driver.

      
 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

