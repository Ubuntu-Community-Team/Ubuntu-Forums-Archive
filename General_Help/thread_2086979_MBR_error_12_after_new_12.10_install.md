---
title: "MBR error 1/2 after new 12.10 install"
date: 2012-11-22
forum: General Help
---

### Post by Quatrix on 2012-11-22
I recently replaced a failing hard drive and copied the partitions to the new drive.  I was having trouble booting Ubuntu, and it was an almost pristine install anyway, so I decided to just reinstall it.  I put Ubuntu on sdb1 and the boot loader on sdb.  After rebooting I get MBR error 1 and then MBR error 2 if I press any key.

Why would this happen after a routine install, and how can I fix it?  This is a multi-boot system with Windows 7 (SSD/sda1), XP, and a second Windows 7 partition.  All disks use MBR, not GPT.

---

### Post by oldfred on 2012-11-22
Are you booting from sdb? Or did you have an old copy of grub in sda and still trying to boot that?

       Post the link to the BootInfo report that this creates.

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Quatrix on 2012-11-22
Boot Repair did the trick, but I'm still curious why it wouldn't boot after a fresh install.  Yes, I was booting from sdb.  The Windows 7 boot loader is on sda.

[http://paste.ubuntu.com/1377979/]("http://paste.ubuntu.com/1377979/")

---

### Post by dcstar on 2012-11-22
> **Quatrix said:**
> Boot Repair did the trick,


Then MARK the thread.

---

### Post by efflandt on 2012-11-23
Grub in 12.10 is somewhat broken in that it initially seems to ignore UUID and tries to find drives by hardware definitions.  So when you install, sdb was hd1, but when you have BIOS boot that drive, grub initially sees sdb as hd0 and cannot find anything it is looking for on whatever is hd1 at that time.

For example when I installed 12.10 on a USB drive sdh, from USB stick on sdg, it configured grub that hd7 was root.  But when I booted the USB hard drive I was dumped to the grub prompt and from ls determined that during boot from the USB (which was then sdg), that drive appeared to be hd0 to grub.  I don't know if that has been fixed in an update for grub to find partitions by UUID like it should be able to, so varying hd numbers will not matter. 

I had to hand edit /boot/grub/grub.cfg on the USB drive to change all instances of hd7 (1st boot) or hd6 (after installing 95 updates) to hd0.  But I have not run it often enough yet to know if update-grub will muck it up again.

---

