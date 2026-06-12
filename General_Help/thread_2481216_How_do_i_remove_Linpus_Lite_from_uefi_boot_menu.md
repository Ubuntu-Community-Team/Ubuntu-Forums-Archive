---
title: "How do i remove Linpus Lite from uefi boot menu?"
date: 2022-11-22
forum: General Help
---

### Post by winduprtma on 2022-11-22
Hello,
I've been trying to figure out on how to remove 'Linpus Lite' from BIOS boot menu settings and leave windows boot manager alone there.

I have already removed ubuntu partition and ubuntu from the efi, it did remove ubuntu boot menu from BIOS boot menu, but somehow the Linpus Lite is still there. 

I've looked into efi directory but i couldn't find the Linpus Lite dir to remove, only '.' directory,  '..' directory,  'boot' directory, and  'microsoft' directory.

Is there a way to fix this? Thank you.

---

### Post by oldfred on 2022-11-22
Is this still an UEFI entry?
You should be able delete from UEFI settings menu, not UEFI boot menu.

If in Linux to see UEFI boot entries.
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

Not sure how from Windows. Probably best to ask that on Windows forum.

---

### Post by yancek on 2022-11-23
Is this an Acer computer which came with Linpus preinstalled?  As pointed out above, there are one time boot options as well as BIOS firmware boot options.  If I recall correctly, the Acer I had some years ago used the F2 key to access BIOS although I don't know that is what is used on your computer.   Many computers will allow you to remove an entry with efibootmgr as described in post 2 above.

---

### Post by sudodus on 2022-11-23
I have a Lenovo computer, that 'thinks' that all bootable USB drives contain Linpus Lite, although I have never used that operating system (not in any computer, not in any USB drive). The text 'Linpus Lite' seems to be hardcoded in the UEFI/BIOS system. (It took a long time until I understood, that Linpus Lite is an operating system; anyway, I am used to that text string and hardly notice it nowadays.)

---

### Post by grahammechanical on 2022-11-23
@sudodus I agree with you.

I have a laptop with an Insyde UEFI and if I want to boot from a USB stick with a Ubuntu ISO image on it I have to select Linpus Lite. Oh well.

Regards

---

### Post by yancek on 2022-11-23
Interesting that people see Linpus on a non-Acer as AFAIK, Acer is the only manufacturer which sold computers with Linpus preinstalled.  Linpus was created with a specific purpose in mind, see link below for basic info, albeit a little outdated and is/was Fedora based.

---

