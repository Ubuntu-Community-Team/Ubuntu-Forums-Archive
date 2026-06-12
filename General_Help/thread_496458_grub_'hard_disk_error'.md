---
title: "grub 'hard disk error'"
date: 2007-07-09
forum: General Help
---

### Post by ian_o on 2007-07-09
After install on my laptop grub reports 'hard disk error' when attempting to boot.

A little research suggested starting the boot on the live cd, then selecting 'boot from 1st hard disk'-  which works perfectly. 
Research has also suggested that the problem is that the hardware as reported by the bios does not match the actual drive spec. There is a suggestion to upgrade the bios which has not solved anything. 
Given that grub actually does work- although right now it needs to be launched with the intermediate step of the live cd- there must be some config setup that allows it to proceed directly? Either hiding the info from the bios (as i suspect the two stage boot using the live cd does) or providing correct drive information directly in a grub config somewhere.
Does anyone have any suggestions?


I tried the /boot/grub/device.map file as a candidate and renaming it did not change anything - exactly the same result. So no device.map at all produces the same result as the current device.map.

Device.map has...
(hd0) /dev/sda
as the only contents.

Any suggestions as to how i can configure things to eliminate needing to use the live CD every time to boot the installed system will be greatly appreciated!! This is very silly needing to have the live cd in the tray just to kick start the boot!

---

### Post by dragonwings on 2007-07-09
first is the hard drive stuft  sometimes they go bad and you cant boot from them but still work good as a slave .

second are you useing ubuntu 7.04 fiesty if not it would be a good idea

---

### Post by ian_o on 2007-07-09
1. No, there is no problem with the hard drive. And recall, it does boot and run perfectly if the live CD is interposed to isolate bios and grub. This same problem has in other cases been solved by a new bios (not a new drive),  so it is clearly software.

2. Yes, i a  using feisty 7.04. I should have stated this, thanks for asking.

Thank you for giving it some thought and replying.

---

