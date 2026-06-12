---
title: "Need help getting Hot-Swap Drive to be recognized in Ubuntu 14.04.4"
date: 2018-06-11
forum: General Help
---

### Post by samq2 on 2018-06-11
[FONT=Calibri]My computer specs are: (a 7 year, 7 month old personal build)[/FONT]
[FONT=Calibri]OS= Ubuntu 14.04 LTSand also Win7 (both OS's on seperate physical hard drives selectable by grub bootloader)[/FONT]
[FONT=Calibri]Memory= 7.8GB[/FONT]
[FONT=Calibri]Processor= Intel Corei5 CPU 750 @2.67 GHZ x 4[/FONT]
[FONT=Calibri]Graphics = Gallium0.4 on NVC3 (supports dual monitors)[/FONT]
[FONT=Calibri]OS type= 64 bit[/FONT]
[FONT=Calibri]Motherboard = MSIP55-GD65[/FONT]
[FONT=Calibri]Case= Antec LanboyAir[/FONT]


[FONT=Calibri]I purchased a Hot-Swap moblle HDD Rack from [http://]("https://www.newegg.com/Product/Product.aspx?item=N82E16817998010&nm_mc=AFC-C8Junction&cm_mmc=AFC-C8Junction-VigLink2-_-na-_-na-_-na&AID=12087162&PID=8167372&SID=ji9mc4345c000a1705278&utm_medium=affiliates&utm_source=afc-VigLink2") to use it for booting to different OS's. [/FONT]

[FONT=Calibri]I installed it just fine and the green LED on the swap caddy is on, but the Hot swap hard drive (a1 TB WD Black 3.5" performance hard drive) is not being recognized byLinux 14.04 LTS OS nor Win7. [/FONT]

[FONT=Calibri]I placed the Hot-SwapHDD Rack in the 5.25" bay that was formally occupied by a CD/DVD drive which is more or less obsolete nowdue to flash/thumb/pen/stick drives, so the cabling was already in place.[/FONT]

[FONT=Calibri]I now have 2 HDD's(Win 7 and Linux 14.04) + 1 Hot-swappable HDD installed. I can boot to theLinux or Win7 drives via a grub bootloader.[/FONT]

[FONT=Calibri]I read something about changing the IDE setting in the BIOS to AHCI instead so the Hot-Swapdrive would be recognized. I did that to no effect.
I confirmed that the AHCI bios setting is correct by  accessing MSI support.[/FONT]

[FONT=Calibri]When I booted my computer initially, the boot failed because the boot sequence in the BIOS hadthe DVD drive as first in the list of bootable devices. I changed the sequence so the Linux drive is first, which causes the bootloader to appear so I can select either Linux or Win7.[/FONT]

[FONT=Calibri]When I first booted from the Win7 drive, Win7 "DID" automatically install the driver for the WD Black Hot Swap drive (partial recognition?!) and referred to it as an"ATA" device although I considered it connected to SATA. After the driver installation was complete, the Hot-Swap drive was not recognized for it did not appear in the windows explorer.[/FONT]

[FONT=Calibri]Linux did not recognize the Hot-Swap Drive either. I'd prefer to have Linux recognize the Hot-Swap Drive rather than win7. There is a procedure in win7 to have the Hot-Swap Drive be recognized.

There must be a procedure to have the Hot-Swap Drive be recognized in Ubuntu 14.04.  The Hot-Swap Drive is brand new, so it's unformatted.[/FONT]

[FONT=Calibri]I'm at a loss for what to do next and am hoping that someone here can guide me to the solution for having the Hot-Swap drive recognized by Linux 14.04.[/FONT]

---

### Post by mörgæs on 2018-06-12
> **samq2 said:**
> [FONT=Calibri]
There must be a procedure to have the Hot-Swap Drive be recognized in Ubuntu 14.04.  The Hot-Swap Drive is brand new, so it's...[/FONT]

... unlikely that old software like 14.04 detects it. Have you tried a live boot of 18.04?

---

### Post by samq2 on 2018-06-12
Ubuntu 14.04 has no problem detecting the Hot Swap drive when I used the Dash to open the "Disks" app. I was able to format the disk this way, but the volume does not appear as a disk icon in the Launcher ribbon, nor does it appear under "devices" when launching the "Files" app.

There must be a way to get the disk device to appear in both the Launcher ribbon and the "Files" app.

Please, does someone out there know the solution?

---

