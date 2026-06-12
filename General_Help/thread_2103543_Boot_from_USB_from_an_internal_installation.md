---
title: "Boot from USB from an internal installation?"
date: 2013-01-10
forum: General Help
---

### Post by groupthinker on 2013-01-10
I have a friend who has a laptop with a bad motherboard. What he's done is remove the hard drive and put it in an enclosure. He'd like to boot off of the now external hard drive from a different computer. What settings need to be adjusted in GRUB2 or in /boot?
As always, any advice is always appreciated.
Ubuntu 12.04

---

### Post by Cheesemill on 2013-01-10
No need to adjust anything, it should just work. All that needs to be done is to tell the new machine to boot from the external drive.

The only issue you may come across is if you have restricted drivers installed for your video card and you attempt to switch from ATI to Nvidia graphics (or vice versa).

---

### Post by Cicer on 2013-01-11
Thanks groupthinker, I'm the friend the OP is helping out. Could it make a difference that the external drive is encrypted?

When booting up and entering the BIOS settings, I do see a drive labeled usb (but listed under "Hard Drives" after the computer's main drive), but I can't change its place in the boot order and when I block the main drive from booting and try to start up, BIOS jumps to the next entry in the hierarchy, boot from network device.

When I go to grub's boot list, the drive doesn't appear as an option at all.

When I have the drive plugged in and run "update-grub", the drive isn't detected as bootable, either. But disk utility describes the drive as bootable.

---

