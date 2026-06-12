---
title: "Help! boot stop at stage 15 grub 17"
date: 2006-11-24
forum: General Help
---

### Post by Azyx on 2006-11-24
I just start my machine with dual boot win2000/ubuntu 6.10 and it dont go till GRUB. stop at stage1.5

I have dual boot win2000/Ubuntu 6.10 and I have run it for several weeks with no problem before

What can I do?

---

### Post by deepwave on 2006-11-24
Please post the exact message given by grub.

---

### Post by Azyx on 2006-11-24
_____________

Searching for Boot Record from IDE-0..OK
GRUB Loading stage1.5.


GRUB loading, please wait...
Error 17

_
____________

This is what the sceen says. and then nothing happens
/Azyx

> **deepwave said:**
> Please post the exact message given by grub.

---

### Post by deepwave on 2006-11-24
From what I gather, Error 17 is when GRUB finds a partition, tries to boot from it and fails.

Usual causes:
- calling SCSI/USB drives with sda1 instead of the proper hd(0,1) hd is for any harddrive regardless of bus type, 0 = a, 1 = b..., and the last one is for the partition.
- GRUB expects one filesystem and then finds another.

Maybe you should look at your /boot/grub/menu.lst file.  GRUB uses this file at startup and for configuration.

---

### Post by Azyx on 2006-11-24
Ok. I am not familiar to go in to a system without a boot disk ;) May I use a 6.04LST disk? and check? Don't it coming problems with priviliges if I use another disk? Ok. I maybe can find it out on other places, but I whould be wery happy with a quick help =)
I don't have any USB/SCSI or external stage device on this machine.

Do Ubuntu use to change in menue.lst by it self? It have worked before, and I have not being in /boot/GRUB/menue.lst for month.(I'm afraid that the hdd is ****** up).

> **deepwave said:**
> From what I gather, Error 17 is when GRUB finds a partition, tries to boot from it and fails.

Usual causes:
- calling SCSI/USB drives with sda1 instead of the proper hd(0,1) hd is for any harddrive regardless of bus type, 0 = a, 1 = b..., and the last one is for the partition.
- GRUB expects one filesystem and then finds another.

Maybe you should look at your /boot/grub/menu.lst file.  GRUB uses this file at startup and for configuration.

---

### Post by Azyx on 2006-11-25
After I read yours replay I boot with Ubuntu 6.10 alternative bootCD and choose "rescue a broken system". I have in this machine hda,hdb and hdd. hda have dualboot, but when i after choosing "rescue a broken system"  i have:
/dev/hda1
/dev/hda2
/dev/hdb1
/dev/hdd1

To choose to have as root file system. I thougt I would choose the partition i have Ubuntu on. It don't work. Nothing works 

I choose "Install GRUB" and come to "Partitionatorn?" (Tool to make partition) and see that I don't have any ext3-partition. It's gone?

Is there any virus that can make ext3-partitoin disappear? I mostly run windows on this machine. I dont know what to do :(
/Azyx

> **deepwave said:**
> From what I gather, Error 17 is when GRUB finds a partition, tries to boot from it and fails.

Usual causes:
- calling SCSI/USB drives with sda1 instead of the proper hd(0,1) hd is for any harddrive regardless of bus type, 0 = a, 1 = b..., and the last one is for the partition.
- GRUB expects one filesystem and then finds another.

Maybe you should look at your /boot/grub/menu.lst file.  GRUB uses this file at startup and for configuration.

---

### Post by deepwave on 2006-11-25
Err... I never heard of an ext-3 virus.  Not sure about the Partitionatorn tool you mention.

Also I don't understand that nothing works.  Lets take it one step at a time.

When you power on the computer, without any LiveCDs or anything, GRUB starts.
Does it give you a menu or just the error?

---

