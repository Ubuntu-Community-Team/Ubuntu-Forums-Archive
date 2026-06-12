---
title: "Mouse turns off on start  and stays off until reboot"
date: 2018-04-06
forum: General Help
---

### Post by Robbyx on 2018-04-06
To try to find the solution I ran

dmesg | grep failed

[   42.309493] xhci_hcd 0000:03:00.0: Host halt failed, -110
[  345.493214] hid-generic 0003:051D:0002.0006: usb_submit_urb(ctrl) failed: -22


[https://bbs.archlinux.org/viewtopic.php?id=192969](https://bbs.archlinux.org/viewtopic.php?id=192969)    claims a solution at #2 to the hid-generic failure



> Ok, I found a workaround. You have to go to /etc/default/ and edit the grub file. There you have to insert "usbhid.quirks=0x1B1C:0x1B12:0x20000000" in the "GRUB_CMDLINE_LINUX_DEFAULT=" line

So /etc/default/grub has to look like this:

GRUB_CMDLINE_LINUX_DEFAULT="resume=UUID=376b974a-9cc7-4a48-9e6a-de19471107f2 usbhid.quirks=0x1B1C:0x1B12:0x20000000 quiet splash"

then run "sudo update-grub" and reboot.

Is that the correct UUID for my problem?  I am assuming that the uuID is specifc to the device. I would like to know how to find the correct uuid or do i use the uuid in the answer

Robin

---

