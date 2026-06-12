---
title: "System wont boot when connecting second HDD"
date: 2017-10-24
forum: General Help
---

### Post by linuxyogi on 2017-10-24
Hi,
I have installed Ubuntu on an internal SSD. I also have a HDD. When I installed Ubuntu the HDD was not connected. Now when I connect the HDD the system freezes at the ASUS logo and it wont boot.

Is there a way to connect the HDD without reinstalling Ubuntu ?

I have already selected the SSD at first boot device in UEFI.

---

### Post by deadflowr on 2017-10-24
Check your device boot order.
It's probably set to try booting from the hdd first, and failing since there is nothing there.
You would do this, normally, in the BIOS/UEFI setup menu which you can typically access at startup (machine startup)
(Most machines almost always give you the key to press when you start the machine to access the BIOS setup, usually something like F2 or whatever.)

---

### Post by linuxyogi on 2017-10-24
> **deadflowr said:**
> Check your device boot order.
It's probably set to try booting from the hdd first, and failing since there is nothing there.
You would do this, normally, in the BIOS/UEFI setup menu which you can typically access at startup (machine startup)
(Most machines almost always give you the key to press when you start the machine to access the BIOS setup, usually something like F2 or whatever.)

I have already selected the SSD as first boot device. Any other ideas ?

---

### Post by linuxyogi on 2017-10-24
I just reconnected the HDD but found that it is not getting detected in bios. I guess its either a compatibility issue or the drive is dead.

---

### Post by oldfred on 2017-10-24
When you disconnect a drive, UEFI forgets all the info it had saved in its NVRAM on booting from that drive.
You may just need to use efibootmgr to recreate boot entries.
But UEFI should still see drive in list of drives, not necessarily in list of bootable devices.

---

### Post by linuxyogi on 2017-10-25
> **oldfred said:**
> When you disconnect a drive, UEFI forgets all the info it had saved in its NVRAM on booting from that drive.
You may just need to use efibootmgr to recreate boot entries.
But UEFI should still see drive in list of drives, not necessarily in list of bootable devices.

The drive is not shown in SATA devices list. This is total new hardware. Dont want to play with it too much. I will just use my SSD.

---

### Post by oldfred on 2017-10-25
If not in SATA drive list in UEFI/BIOS then no operating system will be able to find it.
First check connections, cables and also see if any other system can see drive.
If not drive may have failed.

---

