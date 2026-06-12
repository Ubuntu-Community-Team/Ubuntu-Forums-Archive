---
title: "Ubuntu boot up lost"
date: 2008-07-05
forum: General Help
---

### Post by rawhide1931 on 2008-07-05
Hi All,
      I have Xp pro and Ubuntu on my harddrive,after an update on XP I found my boot on the bios for ubuntu had dissapeared.

      I followed instructions for making a boot disc but windows wouldnt accept the command to write to the floppy.

      Any ideas in simple English how I can get to boot in again as I dont really want to have to reload it all again.

                  Thanks.

---

### Post by louieb on 2008-07-05
How did you install Ubuntu? wubi in windows or in its own partition?

---

### Post by rawhide1931 on 2008-07-05
> **louieb said:**
> How did you install Ubuntu? wubi in windows or in its own partition?

On its own partition but now it doesnt show up in the bios to let me log on.

---

### Post by falcon61102 on 2008-07-05
Were you using the Windows boot loader or GRUB?

If you were using the Windows boot loader, you may just have to edit the boot.ini file on your c: drive because it may have been overwritten by the update you installed.

If you were using GRUB, the update may have overwritten your MBR and replaced GRUB with the windows boot loader.  If you have a Ubuntu Live CD you can boot Ubuntu from that and re-install the GRUB back to your MBR.

---

### Post by louieb on 2008-07-05
Sorry but I don't know what a boot on BIOS is.   As falcon61102 asked we really need to know what boot loader you a using. (Windows or GRUB). Can you describe exactly what the computer does at boot?  Do you get a boot menu? Does it boot straight to windows?  What does the boot menu look like? 

IF you have internet with the live CD please post the partition table. Applications>Accessories>Terminal and post the output of```
 sudo fdisk -l
``` (lowercase L at the end)

---

