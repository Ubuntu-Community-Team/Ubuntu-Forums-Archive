---
title: "Boot From USB Stick To Ext. HardDrive"
date: 2008-02-16
forum: General Help
---

### Post by Zizzech on 2008-02-16
Here it is:
I installed Ubuntu to my External HardDrive (125GB for NTFS, 120GB for EXT3, 5GB for SWAP)
Partition1 is EXT3
Partition2 is NTFS
Partition3 is SWAP

I removed GRUB from the MBR
Is there a way I can use a USB Stick to have my computer boot from the Partition1 of my External HardDrive?
(Laptop doesn't allow me to boot from External HardDrive(Dunno Why))

---

### Post by dcstar on 2008-02-16
> **Zizzech said:**
> Here it is:
I installed Ubuntu to my External HardDrive (125GB for NTFS, 120GB for EXT3, 5GB for SWAP)
Partition1 is EXT3
Partition2 is NTFS
Partition3 is SWAP

I removed GRUB from the MBR
Is there a way I can use a USB Stick to have my computer boot from the Partition1 of my External HardDrive?
(Laptop doesn't allow me to boot from External HardDrive(Dunno Why))

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

You should be able to modify it to boot off the hard drive straight away.

---

### Post by mdurham on 2008-02-16
> 
(Laptop doesn't allow me to boot from External HardDrive(Dunno Why))

If it can't boot from an External HardDrive will it be able to boot from a USB Stick?

---

### Post by Zizzech on 2008-02-17
Yes

---

