---
title: "Grub and external hard drive"
date: 2006-09-14
forum: General Help
---

### Post by rekahsoft on 2006-09-14
Hi all...i am trying to get windows xp to boot off any externel hard drive and am having some problems...it says that there is read/write errors when i try to boot into it...here is my /boot/grub/menu.lst (that is partaining to my problem):```
# Divider
title		Gaming OS:
root

title		Hell is Removable
root		(hd1,1)
map		(hd0) (hd1)
makeactive
chainloader	+1
```Is there anyway to get windows xp to boot off an external hard drive? My motherboard has to support booting from USB right? how do i find out if it can? Thanks...I was windows free for 4 months but want to play some games from time to time so i want to put windows on an external drive...anyways...some mroe helpful information might be that i copied the partition using Partition magic (because GParted does not support copying ntfs) and it sayed somthing about how the partition would not be bootable...is that my problem? Thanks

---

### Post by kidders on 2006-09-15
Hi there,

Unfortunately, your problem could be *loads* of things :-( What error message does grub spit at you?

The handiest way to find out whether your BIOS supports booting from external devices is to try to re-order your boot disks, so your USB device is first on the list. Assuming your original Windoze system partition is still flagged as bootable, your PC should bypass grub altogether and boot into Windows for you. If you can't get that much to work, afaik there's very little point in proceeding further.

Assuming you *can* persuade that much to work for you, your next job is to fiddle with your grub configuration until it works too. Grub is a lifesaver in that respect, because it will let you modify your boot parameters from the boot menu itself (unlike many other bootloaders). Switch your boot order back the way it was, and keep editing & re-editing grubs command sequence until you find something that cooperates. Then make your changes permanent by adding them explicitly to your menu.lst.

Once you're done, grub *should* be happy to boot from a USB device for you.

---

### Post by rekahsoft on 2006-09-15
Well that sucks...i can't boot to usb...not to mention that the boot flag is taken off...well...that is the end of that idea...thanks

---

