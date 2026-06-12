---
title: "Windows boot option not found?"
date: 2023-02-08
forum: General Help
---

### Post by aioont on 2023-02-08
I have a dual booted windows and latest stable Ubuntu version. I do 'sudo rm -rf /' to remove Ubuntu.But now my windows boot option not showing in BIOS. I disabled safe boot and fast boot, changed boot priority - Ubuntu as first option.How can I boot into windows ? Please help me

---

### Post by howefield on 2023-02-08
Thread moved to the "*General Help*" forum.

---

### Post by tea for one on 2023-02-09
> **aioont said:**
>  I do 'sudo rm -rf /s' to remove Ubuntu.But now my windows boot option not showing in BIOS. I disabled safe boot and fast boot, changed boot priority - Ubuntu as first option.How can I boot into windows ?
Having removed Ubuntu, setting Ubuntu as first option would be an unusual decision.

Can you not reach the one-time boot menu via the dedicated key (Esc, F2, F10, F12 etc) and select Windows?
Failing that, you'll will have to make a Windows repair usb and use Windows tools to fix the boot manager.
Image attached.

---

### Post by Impavidus on 2023-02-09
I'm not sure what you did. Your command would have removed the /s directory and all its contents, but on a normal system that directory doesn't exist, so that command would've done nothing. And rm without --no-preserve-root would refuse to work on / anyway.

In any case, deleting all files from Ubuntu doesn't remove Ubuntu; it just breaks it. The partition is still there. If you also removed all files from the EFI partition (which is normally mounted in Ubuntu, so accessible for the root user), that would have removed all bootloaders, both Linux and Windows. Maybe you need a Windows repair disk.

Boot-repair may give us more information on your system. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yancek on 2023-02-09
I agree with the info in post 4 as I don't see how what you posted could do what you said it did.  If your purpose was to use the previous Ubuntu partition for windows, there was no point in attempting to remove it but simply use windows Disk Management tool to format that partition to a windows filesystem (ntfs).

---

