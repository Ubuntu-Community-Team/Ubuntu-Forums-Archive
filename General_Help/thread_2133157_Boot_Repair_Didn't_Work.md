---
title: "Boot Repair Didn't Work"
date: 2013-04-07
forum: General Help
---

### Post by Dominus123 on 2013-04-07
Hi,

my first post here. Have used Ubuntu/Linux on and off for several years but more an enthusiast.

Anyway sure you heard this a thousand times but here goes "I can't boot Ubuntu".

I have a laptop pre-installed with Win 7. 

I installed Win 8 to dual boot with Win 7. 

System is EFI, GPT partitions.

Installed Ubuntu 64-bit, it installed fine. I created a 20gb partition within windows which I left unallocated space, than installed Ubuntu to this. Chose to mount as '/'.

After installation Ubuntu added the below DUPLICATE entry to BIOS: (Is this normal? Why on earth is there a need to have this twice in Boot options?)

Ubuntu (P0 Hitachi etc.....)
Ubuntu (P0 Hitachi etc.....)

I ran boot repair which has not worked. URL is

[http://paste.ubuntu.com/5685849/](http://paste.ubuntu.com/5685849/)

And the message it gives me is:

"Locked-ESP detected. You may want to retry after creating a /boot/efi partition (FAT32, 100MB, 250MB, start of the disk boot flag). This can be performed via tools such as gParted. Then select this partition via the [Seperate /boot/efi partition] option of [Boot Repair].

So to me this is really silly that Ubuntu is now the default option in BIOS yet I only see Windows 7 and 8 to load. So Ubuntu can load my Windows Systems but not its own. I may as well change BIOS back to 'Windows Boot Manager'.

Anyway, that's the story so thanks if you can help!

---

### Post by oldfred on 2013-04-07
You should not have any secure boot issues which many are having. I have only seen the locked issue with Windows 8 systems and it is something corrupted in the FAT32 efi partition as you should be able to write into a FAT32 partition. 
Some have fixed it with chkdsk, but most have to fully backup efi partition which is a good idea anyway. Delete efi partition. The with gparted create new efi partition formatted FAT32 and with gparted right click manage flags use boot flag to make it an efi partition with gpt partitioning. It will have a new UUID, so grub & fstab entries will have to be updated with Boot-Repair or manually.

 grub-efi fails to install with Input/output error - locked efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)

---

