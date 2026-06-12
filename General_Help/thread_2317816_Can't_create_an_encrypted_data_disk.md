---
title: "Can't create an encrypted data disk"
date: 2016-03-20
forum: General Help
---

### Post by Aries01 on 2016-03-20
Hello

 I am migrating my encrypted data from flash drives encrypted with Truecrypt to ones encrypted using the encryption option of Ubuntu's Disk Utility (LUKS + Ext4). It's an easy job on an old computer with Legacy BIOS, but on a new PC with a UEFI motherboard the process ends with an error message and no useable storage container. Encrypted flash drives formatted on the old PC can however be used without a problem on the new PC. Both computers have the newest 15.10 OS, which apparently comes with all the utilities needed for encrypting drives. Is this problem linked to UEFI?

---

### Post by yetimon_64 on 2016-03-20
What procedure or guide are you using to encrypt the usb sticks? I have several sticks set up with luks and ext4 formatting on a UEFI machine with no problems. You don't mention the applications or method you are trying to use or if you are following instructions etc from elsewhere. 

Although I am on 14.04 I have no trouble setting up luks encrypted drives on this UEFI machine, I doubt it is the UEFI that is causing the errors more likely a procedural problem.

[[COLOR=#0000ff]--This--[/COLOR]]("http://longair.net/blog/2011/04/11/making-an-encrypted-partition-on-a-usb-drive/") is a simple guide I followed to set up luks and ext4 usb sticks. Pretty simple procedure, towards the end it shows you how to unmount the volume and set a label name rather than relying on uuids for identification.

Edit: just noted the tag on the thread shows you are using disk utility. Mine are set up directly from the terminal with the "luksformat" command not with the disk utility.

---

