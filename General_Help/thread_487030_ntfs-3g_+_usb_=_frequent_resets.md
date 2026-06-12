---
title: "ntfs-3g + usb = frequent resets?"
date: 2007-06-28
forum: General Help
---

### Post by Zaggy on 2007-06-28
I have this hdd enclosure attached to my pc with usb, ntfs partition on it, mounted with ntfs-3g.
When copying/reading large files, usb resets a lot:

Jun 28 21:46:35 AMD3200L kernel: [  887.713825] usb 5-1: reset high speed USB device using ehci_hcd and address 3
Jun 28 21:47:26 AMD3200L kernel: [  939.513866] usb 5-1: reset high speed USB device using ehci_hcd and address 3
Jun 28 21:55:03 AMD3200L kernel: [ 1395.868919] usb 5-1: reset high speed USB device using ehci_hcd and address 3
Jun 28 21:55:33 AMD3200L kernel: [ 1426.293968] usb 5-1: reset high speed USB device using ehci_hcd and address 3
Jun 28 22:02:31 AMD3200L kernel: [ 1844.100768] usb 5-1: reset high speed USB device using ehci_hcd and address 3
Jun 28 22:03:02 AMD3200L kernel: [ 1874.713851] usb 5-1: reset high speed USB device using ehci_hcd and address 3
Jun 28 22:03:32 AMD3200L kernel: [ 1905.003123] usb 5-1: reset high speed USB device using ehci_hcd and address 3
Jun 28 22:04:05 AMD3200L kernel: [ 1937.187250] usb 5-1: reset high speed USB device using ehci_hcd and address 3

Anthing I can do to circumvent/fix this?

---

### Post by Zaggy on 2007-07-13
bump

---

### Post by stchman on 2007-07-13
> **Zaggy said:**
> I have this hdd enclosure attached to my pc with usb, ntfs partition on it, mounted with ntfs-3g.
When copying/reading large files, usb resets a lot:

Jun 28 21:46:35 AMD3200L kernel: [  887.713825] usb 5-1: reset high speed USB device using ehci_hcd and address 3
Jun 28 21:47:26 AMD3200L kernel: [  939.513866] usb 5-1: reset high speed USB device using ehci_hcd and address 3
Jun 28 21:55:03 AMD3200L kernel: [ 1395.868919] usb 5-1: reset high speed USB device using ehci_hcd and address 3
Jun 28 21:55:33 AMD3200L kernel: [ 1426.293968] usb 5-1: reset high speed USB device using ehci_hcd and address 3
Jun 28 22:02:31 AMD3200L kernel: [ 1844.100768] usb 5-1: reset high speed USB device using ehci_hcd and address 3
Jun 28 22:03:02 AMD3200L kernel: [ 1874.713851] usb 5-1: reset high speed USB device using ehci_hcd and address 3
Jun 28 22:03:32 AMD3200L kernel: [ 1905.003123] usb 5-1: reset high speed USB device using ehci_hcd and address 3
Jun 28 22:04:05 AMD3200L kernel: [ 1937.187250] usb 5-1: reset high speed USB device using ehci_hcd and address 3

Anthing I can do to circumvent/fix this?

I recommend using FAT32 for your external hdd.  It is able to me mounted and edited by any OS.

---

### Post by szaka on 2007-07-13
This issue is file system independent and it's either a hardware problem or kernel bug. It's impossible to tell without your full log. Maybe you have a Seagate FreeAgent or similar USB drive which likes to randomly power down. You need to use a special tool on Windows to disable such "features".

---

### Post by deathspell on 2007-07-13
I have a question. I installed the NTFS-c using Add/Remove

Its working without any problems but I just noticed that the one that says on the official website is the most stable version isn't the one that I got.

It says I have[SIZE="2"]** ntfs-config 0.5.5**[/SIZE]

Do I need to manually download the source and compile it if I want the latest version? Why doesn't add/remove have the latest version? I have been a little worried about writing to NTFS partitions but the support channel on IRC said its totally safe to do so as its stable. I didn't know until now that the version I have is not the recent one.

---

### Post by szaka on 2007-07-14
> **deathspell said:**
> Do I need to manually download the source and compile it if I want the latest version? Why doesn't add/remove have the latest version? I have been a little worried about writing to NTFS partitions but the support channel on IRC said its totally safe to do so as its stable. I didn't know until now that the version I have is not the recent one.
Please submit an Ubuntu bug report.

---

