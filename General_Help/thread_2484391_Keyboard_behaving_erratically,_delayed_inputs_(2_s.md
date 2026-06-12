---
title: "Keyboard behaving erratically, delayed inputs (2 seconds), repeated key entries, etc."
date: 2023-02-24
forum: General Help
---

### Post by xanizen on 2023-02-24
This problem happened shortly after I transferred large swaths of data between hard drives (over 1 terabyte), and used Veracrypt to define new encrypted partitions. This was due to acquiring a new hard drive for backing up files, and to convert filesystems from exFat/NTFS to ext4.
[B]
Example of repeated entries[/B]: you press the F key, then 1 second later you get, 'ffffffffffffffffff'.

The worst case happened, where I unplugged they keyboard from the main computer, and connected it to a ThinkPad laptop with the same operating system, Ubuntu 22.04. After using the keyboard on the laptop for an hour I connected it back to the system. It functioned normally on the main system. Then 5 minutes later no response at all. The only solution was to unplug it and then plug the USB to a different slot, one that used the 'header' ([Amazon Link]("https://www.amazon.com/BAIRONG-Internal-Motherboard-Header-Female/dp/B097GHT5N4/ref=sr_1_3?crid=21QDME0HYLM38&keywords=usb+internal+cable&qid=1677282794&s=electronics&sprefix=usb+internal+cable%2Celectronics%2C317&sr=1-3")), then keyboard functions normally.

I followed the advice of this thread, and the USB settings were where they're supposed to be:
[https://ubuntuforums.org/showthread.php?t=2287740&p=13360525#post13360525](https://ubuntuforums.org/showthread.php?t=2287740&p=13360525#post13360525)

UEFI-BIOS configuration are:
Legacy USB support: Enabled
Intel xHCI Mode: Smart Auto
EHCI Hand-of: Disabled

The main system, a desktop, is an Intel 1150 chipset with Platform Controller Hub, Z87. There are two distinct USB connections, the slots located directly on motherboard, where audio-jack, hdmi and ps/2 ports are located, and then where one connects their computer case to the motherboard 'USB header'.

**My theory/question** is whether the amount of file transfer caused some sort of build up in a 'cache', and thus impeding Ubuntu/Xorg's ability to interpret keyboard commands?

Mouse is behaving normal. I had an issue 3 months ago, on Windows 7, where the 6 month old mouse would erratically click on stuff or the cursor would move on its own to the upper left hand corner AND left click, all on its own; this happened in conjunction with keyboard repeating keys. Replacing the power supply seemed to have fix the problem. This is when I replaced the keyboard, with a wireless one, before I got the power supply.
[https://forums.tomshardware.com/threads/pc-is-repeating-letters-same-issue-with-different-keyboards.3325725/](https://forums.tomshardware.com/threads/pc-is-repeating-letters-same-issue-with-different-keyboards.3325725/)


The keyboard in question has new batteries in it, and as noted. No problem on the ThinkPad laptop.

---

