---
title: "Laptop wont boot after using boot repair"
date: 2024-09-06
forum: General Help
---

### Post by caterhamfan on 2024-09-06
I was using boot repair to fix a windows 11 install that was not showing on the grub screen (dual boot).

I don't know the settings I selected, but now when I boot in I see this!
[I]
alert /dev/mapper/ubuntu--vg-ubuntu--lv does not exist[/I]

[IMG]https://photos.app.goo.gl/y2kZoGxAA6ZpXAd49[/IMG]
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294208&stc=1[/IMG]

My boot repair paste - [https://paste.ubuntu.com/p/4Fy6yg2hWN/](https://paste.ubuntu.com/p/4Fy6yg2hWN/)

Similar to [this]("https://askubuntu.com/questions/843109/alert-dev-mapper-ubuntu-vg-root-does-not-exist") but not the same.
I would be grateful for any help with this. I am pulling my hair out.

Thank you

---

### Post by oldfred on 2024-09-06
I do not know LVM.
But your grub in sda2 is looking for an UUID that does not exist.
You need a full reinstall of grub. If you mount LVM, you probably can use Boot-Repair's advanced mode or full chroot.
chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)

Your Windows install does not look correct.
You show no UEFI boot entry, no Microsoft folder in any ESP and no system reserved. Also it usually as several recovery partitions.  But drive is gpt which Windows requires for UEFI boot. It almost looks more like an very old BIOS install, but then Windows requires MBR(msdos) partitioning. 
Did you attempt to copy an old BIOS/MBR install to a new UEFI/gpt system?
Probably best to backup data and totally reinstall Windows.

---

