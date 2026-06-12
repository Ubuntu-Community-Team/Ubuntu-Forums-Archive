---
title: "Can't launch without nomodeset, low resolution, partition got corrupted."
date: 2017-04-20
forum: General Help
---

### Post by Hopeatykki on 2017-04-20
I created a 30GB partition off my hard drive to install ubuntu on it. Everything went fine, but as soon as I tried to boot, it only showed me black or a colored screen, every time a different color. I googled a bit and I fixed it by replacing something with "nomodeset". Then I encountered other problems. My resolution was locked to very low, I couldn't install GPU drivers (although I don't know if I even had the right one) and ubuntu wasn't detecting my graphics card. I had set first boot option as GRUB, but it instantly booted into Windows 10, so I tried to directly boot into GRUB, but it said that there was nothing to boot.

SPECS : 
Intel i5 4460
GTX 970
16GB Ram
128GB SanDisk SSD
1TB WD Blue

---

### Post by oldfred on 2017-04-20
What motherboard.
Some have settings in UEFI on which video mode is used.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by pete-br on 2017-04-26
I would like to establish if you are using UEFI or BIOS mode.
Linux can handle different scenario's, Windows however is always using:
Windows in UEFI mode: GPT disk
Windows in BIOS mode: MBR disk

Just boot to Windows and open a command prompt.
Give the command 'diskpart'.
It will ask for elevation of access rights, so approve.
then type 'list disk' without quotes.
Here is an excellent example if how that would look:
[http://www.disk-partition.com/windows-10/images/diskpart-windows-10-1203_tmp/list-disk.jpg](http://www.disk-partition.com/windows-10/images/diskpart-windows-10-1203_tmp/list-disk.jpg)
Look for an asterisk (that is this sign: *) in the gpt-row.
If an asterisk is present, your disk is gpt partitioned and you are using EUFI.
If not, your disk is mbr partitioned and you are using BIOS
Type 'exit' to close diskpart.

I am guessing your SSD disk is your bootdisk and the 1TB disk is for data only.
In that case, ignore whatever the HDD is showing and only look at information for your SSD disk.


So with the asterisk is using GPT, means EUFI. Without is using MBR, means BIOS.
You should boot from your Live CD in the same mode as you are using to boot into Windows.
This could mean you have to disable secure boot in the EUFI settings.
The same goes for your installed Ubuntu, always make sure you stay with the same boot mode everywhere.
If you didn't that might be the reason why you could boot into Ubuntu, I would suggest to reinstall properly.

---

