---
title: "Partition / Windows Installation"
date: 2012-12-10
forum: General Help
---

### Post by davidlondon on 2012-12-10
I currently have Ubuntu 10 installed on my girlfriend's laptop and want to revert it back to Windows.

When I try to boot from the recovery disc I get the following pop-up message:

"Error FAIL to get Disk 0 partition 1 drive letter"

I have done some research and have read this is a partition related issue but to be honest I am not that advanced at using partitions on Ubuntiu beyond GPARTEd.

Any advice on how I can resolve would be appreciated.

---

### Post by dannyboy79 on 2012-12-10
so you're trying to boot to a windows xp install disc and completely wipe out ubuntu? It sounds like you didn't choose in the BIOS to boot to the windows xp install disc

---

### Post by davidlondon on 2012-12-10
Yeah I am trying to completely wipe Ubuntu using a the machines recovery disc (Acer laptop originally Windows Vista). I have booted from this disc then it starts to loads the files then the message appears.

---

### Post by oldfred on 2012-12-10
Windows only understands NTFS partitions. Normal installs also want a boot flag on the install partition. Windows does not "see" Linux formated partitions.

Disk 0 partition 1 would be sda1, so is that not a NTFS partition? The recovery will want to restore to the original partition structure and maybe the original partition structure & sizes?

---

### Post by davidlondon on 2012-12-10
At the moment SDA is not a NTFS partition. I will set to  NTFS type and flag as boot and see if that works.

---

### Post by davidlondon on 2012-12-10
Now after running the windows recovery disc on the NTFS partition I get the following message:

error: unknown filesystem
grub rescue>

---

### Post by dannyboy79 on 2012-12-10
thats because grub is still installed into the MBR. I am not sure a computer restore disk will work unless the hard disk is returned to how it was formatted/partitioned like it was when it was purchased. you may need to use a live cd of gparted and wipe out the mbr and partition table before the recovery cd will work.

---

### Post by oldfred on 2012-12-10
If restore otherwise worked, it may not restore MBR as it "knows" it still is the Windows boot loader.

You can use  a Windows repairCD or Linux to put in a Windows work alike boot loader into the MBR.

       How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by davidlondon on 2012-12-11
Managed to get Windows up and running - thanks for the help!

---

