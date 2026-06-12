---
title: "Unable to install 19.10 start_image() returned Invalid Parameter"
date: 2019-11-03
forum: General Help
---

### Post by boyshawn on 2019-11-03
[FONT=Verdana]This is an installation on pure erased laptop (specification at bottom of post).[/FONT]
[FONT=Verdana]I create a bootable USB stick using rufus-3.8.exe based on ubuntu-19.10-desktop-amd64. However, upon loading of the USB drive, there is an error message shown below:[/FONT]
> 
[FONT=Verdana]Could not get fio for li->DeviceHandle: Invalid Parameter[/FONT]
[FONT=Verdana]Failed to get device path[/FONT]
[FONT=Verdana]Failed to find fs: Invalid Parameter[/FONT]
[FONT=Verdana]Failed to load image \EFI\BOOT\grubx64.efi: Invalid Parameter[/FONT]
[FONT=Verdana]start_image() returned Invalid Parameter[/FONT]


[FONT=Verdana][SIZE=3]**[SOLVED]**[/SIZE]
[/FONT]I have managed to solve this. As I was reading online, legacy laptop has to be used with bootable USD with rufus with this option of '**Add fixes for old BIOSes (extra partition, align, etc.)**'. I create my bootable USB stick again with this option checked, and it works now! 

[LIST]
[/LIST]

[FONT=Verdana]The laptop is now blank without any OS. I am sure the laptop is operating well, because I have successfully installed Windows 7 and it ran went before I erase the whole hard disk.[/FONT]

[FONT=Verdana]The model is Fujitsu T901. I have copied the [/FONT][specification]("https://sp.ts.fujitsu.com/dmsp/publications/public/ds-lifebook-t901.pdf")[FONT=Verdana] to below:[/FONT]
[FONT=Verdana]Processor: Intel® Core™ i7-2640M processor (2.8 GHz, 4 MB)[/FONT]
[FONT=Verdana]Memory: 2x 4 GB DDR3, 1333 MHz, PC3-10600, SO DIMM[/FONT]
[FONT=Verdana]Hard disk drives: SSD SATA, 128 GB, 2.5-inch[/FONT]
[FONT=Verdana]WLAN: Atheros Minicard b/g/n, Intel® Centrino® 6205 802.11 a/b/g/n[/FONT]

---

