---
title: "New laptop - transferring SSD from old laptop"
date: 2014-06-18
forum: General Help
---

### Post by David D. on 2014-06-18
I have a new laptop on order to replace an older one.  I currently have 14.04 64-bit installed on an SSD I added to the old/current laptop.  I plan to move the SSD to the new laptop and use the 1TB HHD in the new laptop for data/media storage (it is a large laptop with two drive bays).

I have never worked with UEFI before, so in the long run would it be better to do a fresh installation, or will the current install on the SSD work well in the new laptop?

The old laptop is an HP dv7.  The new laptop is an HP Envy 17t with Intel Core i7-4700MQ, 16 GB RAM, integrated Intel HD-4600 graphics, and a 1TB HDD with Windows 8.1 pro pre-installed.  I am NOT planning to dual boot, Ubuntu will be the sole operating system.

Any hints, tricks or advice on transitioning to the new laptop will be appreciated.

---

### Post by sudodus on 2014-06-18
I have moved HDDs, SSDs and pendrives between computers, and Ubuntu is portable between computers.

If you intend to use only Ubuntu, you need not use UEFI, provided it can be switched off in the computer. Check in the UEFI/BIOS menu system how to switch from UEFI to BIOS (or CSM as it is often called). If you want to run in UEFI, you must also have the GUID partition table (GPT) instead of the old MSDOS partition table.

With BIOS you can use your old drive, particularly if you have no proprietary drivers (typically for graphics and wifi). Otherwise you might have to remove the proprietary drivers (and if necessary install new ones for the new computer). I thinkIntel HD-4600 graphics will run well with a built-in (and free) graphics driver.

-o-

If you want to test without tampering with any internal drive, you can test an installed system in a pendrive, which can run in both UEFI and BIOS mode
[URL="http://ubuntuforums.org/showthread.php?t=2213631"]
Portable installed system that boots in UEFI as well as in BIOS mode[/URL]

Good luck :-)

---

### Post by David D. on 2014-06-18
Thank you for the information and response Sudodus.  I've marked this thread as solved and will start new one(s) if I run into any difficulties I cannot work out myslef or via searches.

---

### Post by oldfred on 2014-06-18
Is second drive bay bootable?

Some with the removeable DVD/ hard drive convertable bay have found that while they can read data from the caddy, they cannot boot from it. Not sure what computer that was but I would check. Most computers now boot from just about anything, but may need setting in UEFI/BIOS to allow it. Secure boot or other lockdown may have been set to prevent booting for security.

---

### Post by David D. on 2014-06-18
Thanks for your comments OldFred.  I will be sure to place the SSD in the drive 1 bay and move the HHD currently there to drive bay 2.

From other posts I have gathered that the secure boot should be disabled in the BIOS to ensure bootability.

---

