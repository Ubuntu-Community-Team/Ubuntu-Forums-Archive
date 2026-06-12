---
title: "Ubuntu suddenly won't boot, like SSD isn't there?"
date: 2022-04-10
forum: General Help
---

### Post by technicalsupport55 on 2022-04-10
Hi all,

I am running a 1.5 year old Lenovo IdeaPad. Installed Ubuntu about 6 months ago. Internal SSD, no hard drive. Had no major issues until today.

Today I tried to boot my computer but I only get an error that says that no bootable device was found.

When I look in bios, I see no devices to choose from. 

I can boot from a USB, but I've tried the following with no avail:

1) Removed all devices that night confuse the bootloader.
2) Tried to reinstall Ubuntu (while keeping files) but there is no partition to choose from.
3) Tried the boot repair tool but it said it could not act on the boot.

I am completely at a loss, has anyone else come across this? Is this a hardware or software issue?

---

### Post by Autodave on 2022-04-10
Check your connection to the SSD.  If good, sounds like the SSD has failed.

---

### Post by oldfred on 2022-04-10
Does UEFI setting show the drive, not just the boot menu?
If UEFI/BIOS cannot see a drive, no operating system can do anything.

But if drive seen, it may be some other issue.
Can you see drive from Ubuntu live installer?

---

### Post by technicalsupport55 on 2022-04-11
Ill try. It's a laptop and not easily accessible.

---

### Post by technicalsupport55 on 2022-04-11
The BIOS screen says no device detected next to the "Hard Drive." I can boot Ubuntu from a USB, thought I might use it to do a system repair/reinstall, but when I try that I have no drive or parton to select (other than the USB itself).

So no, I can't see the SSD either in BIOS or in the Ubuntu installer.

---

