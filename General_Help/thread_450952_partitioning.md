---
title: "partitioning?"
date: 2007-05-21
forum: General Help
---

### Post by axemurder785 on 2007-05-21
how do i make it so that when i use my computer windows uses two of my drives, and ubuntu linux 7.04 uses my third one?

---

### Post by kragen on 2007-05-21
Well presumably you will have windows installed on the first (or second) drive, and then an NTFS partition on the second drive. All that remains is to install Ubuntu on the third drive using the standard installer.

At the end of the installer it should prompt you to install GRUB - just install it on the MBR of the first drive (the one with windows on). This will be the drive that boots first, so your computer will boot into grub.

The Installer should then recognise your windows installation, and configure grub with a windows menu option, as well as adding a menu option to boot Ubuntu off the third drive.

Alternatively, I believe you could install grub on the third drive (the one with Ubuntu Installed), however that would require you to go into your computers BIOS to select which drive to boot off every time you wanted to switch OS.

Ultimately, just download the CD and go with whatever seems most logical - if you are unsure, go with the default options, it will warn you if you are likely to break anything, and it's designed to work well for most people.

---

