---
title: "Help. Changing video card killed ubuntu."
date: 2008-06-28
forum: General Help
---

### Post by LocoMan on 2008-06-28
Heeelp.

Basically, I'm changing the video card to ubuntu, used to have an nvidia 7100, changing it to an 8600 that was on my main computer (which I upgraded recently to 8800). Ubuntu was running perfectly, I used Envy to uninstall the drivers, reboot to check that it worked without drivers, then I turned it off, took the old video card out, put the new one in, and Ubuntu now won't start, neither with the new or with the old video card.

When I try to start with the recovery mode, it first stops at:

ata4: failed to recover some devices, retrying in 5 secs

then starts running some more, stops again at

8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)

and then shows some more text and stops at

check root=bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/2de60f01-e2dd-4d01-b917-f38dff1c32fe does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)_

That makes it sound like HD problems, but was running perfectly (actually copied a 12 gigs folder to it last night) with no problems, and I'm guessing that changing a video card shouldn't have done anything to it.

Any help?... also I'd rather not reinstall ubuntu unless it's the last option at all, I spent a while getting it how I want it and installing stuff on it, wouldn't want to have to start all over again.

Oh, and I have 8.04, upgraded from 7.10 last week.

---

### Post by luisito on 2008-06-28
I don't really know what the problem might be, so I am just suggesting a few things to try. Have you checked if /dev/disk/by-uuid/2de60f01-e2dd-4d01-b917-f38dff1c32fe exists or not? Does this uuid coincide with the one in /boot/grub/menu.1st?

If you press esc during boot time and choose the older kernel, does it also happen?

I don't see how any of this would have to do with changing a video card, but who knows.

---

### Post by LocoMan on 2008-06-28
> **luisito said:**
> I don't really know what the problem might be, so I am just suggesting a few things to try. Have you checked if /dev/disk/by-uuid/2de60f01-e2dd-4d01-b917-f38dff1c32fe exists or not? Does this uuid coincide with the one in /boot/grub/menu.1st?

If you press esc during boot time and choose the older kernel, does it also happen?

I don't see how any of this would have to do with changing a video card, but who knows. The folder does exist and it's the same in menu.lst.

Ubuntu does work with the older kernel, though, but the 3D drivers don't (that was one thing I spent a while troubleshoting last week)...

EDIT: It works now. The problem was menu.lst. Basically when I had ubuntu 7.10 I had to add noapic nolapic to the menu.lst to get it to recognize my network card. When I upgraded to 8.04, it wouldn't start until I removed it. Somehow they got back into menu.lst when I changed video card, removed them again and it works now.

EDIT2: any way to change the topic title to add that it was fixed?

---

