---
title: "Can Not Install Ubuntu 22.04.3 on SSD"
date: 2023-09-07
forum: General Help
---

### Post by mountainman70 on 2023-09-07
I have a new 1tb ssd with W 11Pro on it.  This is my first ssd. W 11 boots fine. Trying to install Ubuntu alongside W 11 so I can dual boot Windows & Ubuntu. But it only gives me the option to erase disk and install.  Why doesn't it recognize W 11?

---

### Post by psychohermit on 2023-09-07
Go into Windows and disable fast startup. It doesn't really shut down and does kind of a hibernate.
Go into bios and disable secure boot.

--glenn

---

### Post by mountainman70 on 2023-09-08
> **psychohermit said:**
> Go into Windows and disable fast startup. It doesn't really shut down and does kind of a hibernate.
Go into bios and disable secure boot.

--glenn

Turned both off but Ubuntu still doesn't recognize W 11.

---

### Post by jeremy31 on 2023-09-08
Is CSM enabled in BIOS?  Disable it the boot the Ubuntu ISO

---

### Post by oldfred on 2023-09-08
Windows 11 should update firmware, but make sure UEFI & SSD firmware are most current versions.

What brand/model system?

My Dell with 11th Gen Intel & SSD, just installed with Windows 11 and Secure Boot on.
I did have to turn Windows fast boot off & Windows bitlocker off.

---

### Post by mountainman70 on 2023-09-08
oldfred--It is a Dell 9020 Optiplex with a 1tb ssd & W11 Pro preinstalled that I just bought. All updates are current. Fast Boot & bitlocker & Secure Boot are showing off.

---

### Post by oldfred on 2023-09-08
You said new, but looking up specs shows it came with Windows 8?
Or did Dell reuse model number?

Some older Dell systems, needed Legacy/BIOS/CSM boot mode on, but you still must boot in UEFI boot mode.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

And those older systems needed AHCI mode for drives, default often was RAID or Intel RST. But you have to first install AHCI drivers into Windows.
Not sure with Windows 11. My older Dell, that came with Windows 8, does not qualify for Windows 11. But I have seen were some created unsupported work arounds to install Windows 11.

---

### Post by psychohermit on 2023-09-08
Here's an idea.  Boot a live DVD and partition the drive for Linux. Shrink the Windows partition to make room and set up partitions for /, home, and swap.  Then you should get the option of installing Linux.  Choosing something else from the installer and pointing it to the partitions you have set up.  That ought to work.  That's assuming that it's booting in uefi mode.

--glenn

---

