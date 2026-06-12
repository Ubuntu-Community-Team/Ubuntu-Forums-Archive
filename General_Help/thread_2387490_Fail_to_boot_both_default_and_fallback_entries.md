---
title: "Fail to boot both default and fallback entries"
date: 2018-03-19
forum: General Help
---

### Post by kozhukkatta619 on 2018-03-19
A little background info to the issue that I am facing:
My laptop has grub dualboot with Windows 10 and Ubuntu. My laptop has a built-in keyboard and it's damaged so I bought a USB keyboard to work with my laptop. The USB keyboard was not responding on grub ( I was not able to make any OS selection and I used to just wait till grub timed out and booted Ubuntu).
Following some advice, I edited grub to add 
GRUB_PRELOAD_MODULES="usb usb_keyboard ehci ohci uhci"
GRUB_TERMINAL_INPUT="usb_keyboard&#8221; 
and when I tried restarting the laptop, grub timed out and I got the error as mentioned in the title and it is not booting Ubuntu and it returns back to grub. 
Any suggestions as to how to solve this issue.?
Any help is appreciated.
Thanks

---

### Post by oldfred on 2018-03-20
I do not know correct setting.

But can you get to grub menu and manually edit out changes? Or then test with several alternatives of the changes.

If UEFI, you use Escape key after UEFI but before grub to get grub menu. May have to press more than once to get correct timing.
If BIOS you press and hold shift key from BIOS until grub menu appears.

---

### Post by kozhukkatta619 on 2018-03-20
I cannot get into grub menu because the usb keyboard is not responding in grub.

---

### Post by kozhukkatta619 on 2018-03-20
> **kozhukkatta619 said:**
> I cannot get into grub menu because the usb keyboard is not responding in grub.

> **oldfred said:**
> I do not know correct setting.

But can you get to grub menu and manually edit out changes? Or then test with several alternatives of the changes.

If UEFI, you use Escape key after UEFI but before grub to get grub menu. May have to press more than once to get correct timing.
If BIOS you press and hold shift key from BIOS until grub menu appears.


I cannot get into grub menu because the usb keyboard is not responding in grub.

---

### Post by oldfred on 2018-03-20
Often UEFI has settings to turn on full USB support.
But without keyboard working there is no way I know of.

Grub does have a setting where if you have an abnormal shutdown it should show menu, but you still need keys to edit or change any settings.

---

### Post by kozhukkatta619 on 2018-03-22
so there is basically no way to get the laptop working?:(

---

### Post by oldfred on 2018-03-23
Do not know your system. 
Did USB keyboard work in UEFI settings?
You then may be able to force system to reboot into UEFI.
Try a full cold boot, or power down, remove power from mains, remove battery, and hold power switch for 10 sec or so.
Or see if you can access a total reset set of pins on motherboard (check your manual on detail location) or remove coin battery.

---

