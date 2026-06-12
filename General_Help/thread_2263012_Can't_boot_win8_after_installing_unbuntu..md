---
title: "Can't boot win8 after installing unbuntu."
date: 2015-01-28
forum: General Help
---

### Post by thanhtin1308 on 2015-01-28
Hi everyone, I'm a newbie. I have a problem: I installed ubuntu along with win8 (win8 is installed before), after installed ubuntu I didn't do any thing in win8. After install unbuntu, I can't enter win8, but enter unbuntu OK. How can I fix it? 
[http://paste.ubuntu.com/9928658/](http://paste.ubuntu.com/9928658/)

Thank you.

---

### Post by oldfred on 2015-01-29
Your Windows is in BIOS/MBR mode. But with  Windows 8 you still must make sure you have the always on hibernation or fast boot off.

But you have this error?
>  WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


Usually it is Ubuntu that will not install after a gpt drive has been converted to MBR(msdos) partitioning.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

    Did you use Windows tools to shrink the NTFS partition. If not you may need to use a Windows repair disk or the installer in the repair console to fix Windows.
Was Windows or drive originally UEFI with gpt partitioning?

---

