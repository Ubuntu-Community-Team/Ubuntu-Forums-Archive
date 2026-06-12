---
title: "Ubuntu boot failed + No audio/network/battery + BIOS freeze"
date: 2017-10-26
forum: General Help
---

### Post by natalie3600 on 2017-10-26
Dear Forum Users,


I would like to ask you for help with my new laptop (Kruger&Matz Explore 1403).



[SIZE=1]Specs:[/SIZE]
[SIZE=1]CPU: Intel Atom** x5-Z8350** (4 cores, 1.44-1.92 GHz, 2MB cache)[/SIZE]
[SIZE=1]GPU: Intel HD Graphics[/SIZE]
[SIZE=1]RAM: 4 GB (SO-DIMM DDR3, 1066 MHz)[/SIZE]
[SIZE=1]HDD: 32 GB** SSD eMMC**[/SIZE]
[SIZE=1]Input: 2x **USB 3.0** (USB 3.1 Gen. 1), There are no CD/DVD-ROM![/SIZE]


The laptop came from the shop and had OS installed (no CD/DVD included).
The OS was Windows 8 64-bit (upgradable to Windows 10 from the Desktop).
The OS was upgraded to Windows 10 and worked properly for a few days.

Because of the low specs, I decided to install the newest Ubuntu (17.10 Artful Aardvark 64-bit).

The installation (bootable USB-stick created with Rufus) went good.
After a couple of hours of using I noticed that YouTube had no sound and the video (video progress bar) was sometimes moving ridiculously fast. The speakers test showed that there was no sound at all.

I decided to change the OS to the LTS Ubuntu (16.04.3 64-bit). During the installation it turned out that there was no Internet connection. 
After the installation the battery status bar and Wi-Fi networks were missing.


I decided to install the newest Linux Mint (18.2 Sonya 64-bit) and it also had no sound, battery status and Wi-Fi. 
Now the laptop has Windows 10 64-bit but the tray shows that there are no drivers for network and sound and the battery status bar is missing as well. 
I should add that during the installations of Linux Minut and Windows 10 I experienced some problems with booting. Sometimes none of my three USB-sticks was detected but after a few attempts (Rufus/UNetbootin, NTFS/FAT32, MBR for BIOS or UEFI/GPT for UEFI) I managed to get the installation done. **The USB-stick did not boot automatically (the laptop displayed "ubuntu boot failed") and I had to exit the EFI Shell Version 2.40 and choose the exact file (e.g. bootmgr.efi, bootx64.efi) in the "Boot From File" menu in the BIOS.**






[CENTER]**"The main concern" or how does the process of turning the computer on looks like?**
(_Because of the upload limitations and for your convenient browsing_: [https://imgur.com/a/p1E8D](https://imgur.com/a/p1E8D))

[/CENTER]
- The laptop cannot make to the desktop by itself. Regardless of the OS installed, the first thing I see is **"ubuntu boot failed"** (PIC_1). 
- I see **"EFI Shell version 2.40"** and then I type "exit" (PIC_2).
- If I choose "Continue" (PIC_3), it will go back to "EFI Shell version 2.40".
- If I choose "Boot Manager" (PIC_3), I will see a list of EFI Boot Devices (PIC_4). Choosing any of them results in "ubuntu boot failed" alert.
- If I choose "Device Manager" (PIC_3), I will be able to choose "Primary Video BIOS" between PCI and AGP (PIC_5).
- If I choose "Administer Secure Boot" (PIC_3), the laptop will restart and display "ubuntu boot failed".
- If I choose "Setup Utility" (PIC_3), the laptop will display the traditional BIOS. I should add that in (Boot Configuration in Advance_PIC) I can choose in "OS Selection" between "Windows 8.X" and "GMIN". 
- In order to get to the desktop I have to choose **"Boot From File"** (PIC_3). In the File Explorer (PIC_6) I have to choose my HDD which is "NO VOLUME LABEL" *(Ignore the second one; it is a USB-stick as you can tell from its name "[PciRoot...USB(0x0, 0x0)...]")*. Then I have to go through folders and choose **the exact boot file.**

Note: When I choose "Load Custom Defaults" or "Load Optimal Defaults" and then **"Exit Saving Changes", the BIOS freezes **(I cannot use keyboard but the cursor is moving).

[CENTER]In short: 
(i) The laptop cannot boot automatically neither for the purpose of USB-stick installation nor for the purpose of turning on.
(ii) The laptop has no drivers for audio, network and battery status.
(iii) The BIOS freezes.[/CENTER]



I have never seen that kind of BIOS and experienced such problem.
I would really appreciate help from you because I can only think of one solution and it is the **Darik's Boot and Nuke (DBAN)**.


Thank you from advance
Natalie

---

