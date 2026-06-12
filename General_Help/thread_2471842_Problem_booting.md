---
title: "Problem booting"
date: 2022-02-10
forum: General Help
---

### Post by rhythm24 on 2022-02-10
I recently recover an image from clonezilla, now im triying to start ubuntu donsnt start, only in secure mode, and i cant repare.
What should I do?

---

### Post by oldfred on 2022-02-10
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repaircat](https://help.ubuntu.com/community/Boot-Repaircat)                
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by rhythm24 on 2022-02-11
[Ubuntu Pastebin]("https://paste.ubuntu.com/p/fy8M4msKXV/")
I've entered and I recover files, and now isnot important, but i want to know why this happened.

---

### Post by tea for one on 2022-02-11
> **rhythm24 said:**
> I've entered and I recover files, and now isnot important, but i want to know why this happened.

Regrettably, it would be almost impossible for anybody other than yourself to know why you were unable to boot.

We do not know exactly how the Clonezilla image was prepared and verified. e.g. full disk image or separate partitions or something else?
Nor how the image was restored i.e. same disk, same partitions, larger disk, different machine?
Your Ubuntu disk (sdb) was/is encrypted.
You have Windows mbr (report line 5)
You also have Windows EFI System Partition (report lines 11 - 16)

My guess would be that there was some temporary conflict between the Clonezilla image and/or the encryption.
Also, possible dilemma when you were booting the restored image i.e. old style MBR or newer UEFI.

A lot more information would be needed to provide a reasonable answer and, even then, we would still be guessing.

If I were in a similar position, I would be happy that the files have been recovered successfully.

---

### Post by oldfred on 2022-02-11
You show UEFI installs of Windows & Ubuntu on separate drives, but have a BIOS boot loader in gpt's protective MBR for BIOS boot. 

Windows on gpt will not BIOS boot, not sure how you got a BIOS Windows boot loader into the MBR unless old drive converted to UEFI/gpt with new install of Windows.

---

