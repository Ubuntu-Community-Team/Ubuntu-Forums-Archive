---
title: "Redo rescue has removed grub"
date: 2023-01-30
forum: General Help
---

### Post by caterhamfan on 2023-01-30
Hey all, 

Today I accidentally deleted the desktop folder (permanently not just to the recycle bin).
In my haste to recover the folder, I came across redo rescue which I thought could do the job.

However, after burning it to USB and running it. It seems to have dispensed with my grub loader, leaving me with Windows bootloader. Result = I can login to Windows 10 but my Ubuntu 22.10 install has vanished.

I've tried booting from live USB. Installed boot repair, but the recommended option doesn't even come up to do a repair. I can only get a report. I've even tried going into Windows and tried bootrec through advanced troubleshooting.

I've attempted reinstalling grub, however, I am getting an error because my Ubuntu install is encrypted (it's giving me a LUKS error). I will paste the error here when I replicate it.

I'm lost. What can I do first to boot back into Ubuntu and second to recover my desktop files? 

Be grateful for any assistance. 
Thank you,

---

### Post by oldfred on 2023-01-30
First rule if using encryption is to have really good backups.
That way you can easily reinstall & restore, if it takes more than an hour to repair.

If using Boot-Repair with an encrypted install, you have to decrypt your install so it can see your install. If install otherwise bootable, it may offer to reinstall grub, or you can use its advanced mode to choose the install & drive to install grub. Be sure to boot live installer in same boot mode as your install, BIOS or UEFI. 

You may have to chroot into your install to restore other missing pieces. 
chroot & troubleshooting Full system encryption
[https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting](https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting)
LVM chroot
[http://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i?rq=1](http://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i?rq=1)

---

### Post by caterhamfan on 2023-01-30
> First rule if using encryption is to have really good backups.

This I intended to do but never got round to it. Totally my fault. Working through those steps now. Thank you Oldfred!

---

### Post by caterhamfan on 2023-01-30
I can get back into ubuntu now! Thank you so much for your help.

Can anyone help with any good recovery tools to recover a deleted folder?

Thank you,

---

### Post by oldfred on 2023-01-30
Testdisk and its deeper search or its photorec.
I have used photorec on a small drive. It took overnight to copy to another larger drive. It recovered every file and the same file I have saved multiple times. I did not know which was most current so had to do many compares. It took weeks and convinced me to do better backups.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) & 
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) & 
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

### Post by caterhamfan on 2023-01-31
Thank you so much for the information.

This has taught me a huge lesson regarding backups. I cannot believe I did not have one. I will be making sure moving forward. Testdisk is analysing now. Hopefully, I will be able to recover the data, backup, and reinstall Ubuntu 22.04.

Thank you,

---

