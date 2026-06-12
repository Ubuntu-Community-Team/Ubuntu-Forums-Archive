---
title: "uninstalling"
date: 2008-01-29
forum: General Help
---

### Post by ttmw on 2008-01-29
Im trying to uninstall ubuntu on my laptop, im not using a duel boot and its only ubuntu thats on the comp. I try putting my original windows cd in and nothing happens, it just boots streight into ubuntu again.

Can someone tell me how i uninstall ubuntu off my computer please? Thanks in advance

---

### Post by taurus on 2008-01-29
Have you checked your BIOS again to make sure you have CDROM as the first bootable device?

And if you want to completely erase your harddrive before you install windows again, boot your machine with the Ubuntu LiveCD and use gparted, System -> Administration, and delete all partitions.  Then, format it to ntfs filesystem.

---

### Post by Shazaam on 2008-01-29
Two things you can do. Set the pc's bios so it will boot from the cd first instead of the hard drive. Then boot the Ubuntu livecd and use gparted to delete any partitions. This will NOT get rid of grub if you have it installed to the master boot record (MBR) but you should still be able to boot the Windows install cd and install Windows.
Or, you can do as before and make sure the pc can boot from cd first then boot up with the Windows cd in the drive and do the install.

Can I ask why you are going back to windows?

---

