---
title: "Howto: Use Wubi-netboot to install standard Ubuntu (real partition) without a CD"
date: 2007-04-29
forum: General Help
---

### Post by tuxcantfly on 2007-04-29
**DON'T REPLY HERE, POST ALL QUESTIONS AT [http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540)**

[COLOR="Red"][U][I][B]
UNetbootin NOW HAS ITS OWN WEBSITE AND GUIDE AT [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)[/B][/I][/U][/COLOR]

UNetbootin allows for installation of Ubuntu to a real partition (so it's no different from a standard Ubuntu install), and uses a standard netboot installation, so internet access is needed. The main advantage of UNetbootin over Wubi and similar projects is that it creates a standard ubuntu install without needing a CD. However, if you already have installed using Wubi, just use LVPM to transfer the installation over to a real partition, details at [http://lubi.sourceforge.net/](http://lubi.sourceforge.net/)

**Purpose**

This is meant for people who want to install Ubuntu but don't have a CD-R to burn, lack a CD writer, or they want to install on a computer that doesn't have a CD-ROM drive, like an ultra-portable laptop.

**What it does**

UNetbootin uses an Windows-based or Linux-based installer to install a small modification to the Windows or Linux bootloader (grldr and boot.ini for NT-based systems, grub.exe and config.sys for Win9x, or grub for Linux), uses the bootloader to boot the netboot initrd and kernel, then uses that to download and install Ubuntu directly from the internet, no CD required. After Ubuntu is installed, the modification to the bootloader is then undone, 
[B]
Requirements/Dependencies[/B]

Linux or Microsoft Windows 95-XP (Vista support is in the works)
A broadband internet connection (dial-up will take way too long to download)
3GB or more of spare hard drive space to install Ubuntu in

**Installation Instructions**

Before installing, remember to back up all your data, in case you do something wrong in the partitioning stage of the installer.

1. Download the appropriate file for the distro version you want to install; if using an Ubuntu or Debian-based distro, use the deb files, if using another Linux distribution, use the sh (self extracting) files, if using Windows, use the exe files:
[http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=240555](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=240555)

2. Run the file, and click "OK" to reboot

3. Select "Ubuntu" from the menu list

4. Answer the questions asked by UNetbootin, and wait while it downloads and installs 650 MB of packages

5. Reboot, select Ubuntu, and enjoy your new Ubuntu system

**Removal Instructions**

1. To undo the changes to the Windows bootloader, simply boot Windows, and the uninstaller should begin. Press "OK", and it will undo the changes, or uninstall manually from "Add/Remove Applications"

2. To remove Ubuntu itself, see this guide: [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

**Supported Ubuntu Versions**

This has only been tested on 32-bit Gnome Ubuntu 7.04 Feisty Fawn, 6.10 Edgy Eft, and 6.06.1 LTS Dapper Drake, though it should work on any other Ubuntu version; simply run the installer, and replace C:\wubi\initrd.gz and C:\wubi\linux with the netboot initrd/kernel of whatever version you please, then reboot. Netboot initrd files are available for download at [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

**License/Source Code**

This is licensed under the GNU GPL. Source code is available at [http://www.cutlersoftware.com/ubuntusetup/wubi/downloads/experimental/wubinetboot.nsi](http://www.cutlersoftware.com/ubuntusetup/wubi/downloads/experimental/wubinetboot.nsi) and the rest can be obtained from the Ubuntu netboot initrds, grub4dos, and Wubi.

**Credits**

This guide was written from scratch by me. The installer was created using NSIS [http://nsis.sourceforge.net/Main_Page](http://nsis.sourceforge.net/Main_Page) the bootloader came from grub4dos [http://grub4dos.sourceforge.net/](http://grub4dos.sourceforge.net/) and the netboot initrd/kernel came from Ubuntu.

**Known Issues**

Windows Vista is not supported due to its new bootloader which is incompatible with grub4dos

If you encounter errors on reboot such as "Error 17" or "File not found" at the grub screen, try defragmenting your hard drive and running chkdsk

If you encounter errors following the bootup and during the operation of the debian-installer, consult the netboot initrd, debian-installer, and ubuntu installation howtos and documentation

If you encounter errors in Ubuntu, consult the general ubuntu documentation and the forums

If you encounter errors in the Windows portion of the installer, post a question here

Use this guide at your own risk.

---

