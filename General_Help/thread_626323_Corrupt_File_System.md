---
title: "Corrupt File System?"
date: 2007-11-28
forum: General Help
---

### Post by pyro32 on 2007-11-28
I made a big mistake and deleted a file on my linux partition through Windows. I should have thought about it but I didn't and now I am stuck dealing with the mess I have created. The symptoms first occur when I turn my laptop... the grub boot loader menu is corrupted. (Grub is installed on my linux partition) I can still chose the entry for Windows based on the order I know it is in but the list itself is a collage of meaningless characters. I am not given any errors except when I choose the ubuntu partition from the menu, the caps lock key starts flashing. Kernel error?  From the recovery mode on the ubuntu install cd, i can mount the root partition and can display files and directories fine. I looked inside the menu.lst file and found a bunch of misplaced data at the end of the file. This would explain the crazy boot menu. Does anyone have any suggestions for recovering this system?

---

### Post by joe.turion64x2 on 2007-11-28
> **pyro32 said:**
> I made a big mistake and deleted a file on my linux partition through Windows. I should have thought about it but I didn't and now I am stuck dealing with the mess I have created. The symptoms first occur when I turn my laptop... the grub boot loader menu is corrupted. (Grub is installed on my linux partition) I can still chose the entry for Windows based on the order I know it is in but the list itself is a collage of meaningless characters. I am not given any errors except when I choose the ubuntu partition from the menu, the caps lock key starts flashing. Kernel error?  From the recovery mode on the ubuntu install cd, i can mount the root partition and can display files and directories fine. I looked inside the menu.lst file and found a bunch of misplaced data at the end of the file. This would explain the crazy boot menu. Does anyone have any suggestions for recovering this system?
How did you manage to access a Linux partition from Windows? (I know it is possible and it could help solve your problem). Do you mean you deleted the entire "/" partition?

---

### Post by pyro32 on 2007-11-29
I used a program called IFS Drives that installs a kernel driver for ext3 support. It is not get fully compatible with vista... (what is) and it is fine for editing files but this is the first time i tried deleting some music files from a library on my linux partition.

---

### Post by pyro32 on 2007-11-30
I was finally able to run fsck from the live CD and correct the many fs errors... next the grub boot loader menu would not appear, just text based input. I booted back into live CD and found that menu.lst had been renamed to menu.lst~ and was full of completely corrupted data. I used a backup of menu.lst to replace the missing file. Now the menu comes up but when I try to boot Ubuntu, I get "error 15 - File Not Found" from grub. Any suggestions now?

---

### Post by PmDematagoda on 2007-11-30
Is the boot entry for Ubuntu correct and are all the files that it mentions present?

---

### Post by Sef on 2007-11-30
> 15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.

I would download and use [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/") and see if that works.

---

### Post by pyro32 on 2007-11-30
Thanks for the suggestions... I tried the Super GRUB Boot Disk but I all found was that the file that seems to be missing is initrd.img which I understand is partially responsible for the ram drive that is used during bootup. I do have a backup of this file... Where should the file be and is it normal that these files would be missing after a corrupt file system? Am I going to have all kinds of missing files even if I can start the boot process?

---

### Post by pyro32 on 2007-11-30
Ok I replaced the initrd.img file with my backup and finally, the system has booted! No errors but some programs will not load and my configurations for awm and compiz are not loading. Is there any way to assess my damage and determine what needs to be reloaded?

---

### Post by pyro32 on 2007-12-05
bump

---

