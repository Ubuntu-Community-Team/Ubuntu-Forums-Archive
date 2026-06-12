---
title: "Grub for four SO and two hard disks"
date: 2013-12-28
forum: General Help
---

### Post by juanma21a on 2013-12-28
Hi!

I have four SO installed in my computer:
sda1 Windows XP
sda5 Windows Server
sdc1 CentOS
sdc3 Xubuntu
 
I generated the grub by Xubuntu and Now I can not run any Windows. My grub shows: Xubuntu, Windows Server and CentOS. But, I can not run Windows XP or Windows Server.

Can anybody help me?

---

### Post by oldfred on 2013-12-28
Best to see details. Do not run a auto fix from Boot-Repair as it will install grub to every drive and you want Windows boot loaders in the Windows drives. You can manually run those type of fixes.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by juanma21a on 2013-12-28
Thanks you.

My BootInfo report is here: [http://paste.ubuntu.com/6654269/](http://paste.ubuntu.com/6654269/)

---

### Post by oldfred on 2013-12-28
You show a Windows entry in your grub menu. It looks like you have installed grub to every drive.
I would not use auto repair with Boot-Repair as it does install one grub to all drives.
You can turn off auto fix and choose in advanced to update one system and install its boot load to a drive. I would chose your Windows in sda1 and install the Windows (type) boot loader to sda.

If you cannot see Windows entry in grub menu it may be because you have lots of entries. You do you have a tiny arrow down at bottom right of grub menu box. Then you can scroll down for more entries.

Windows only boots directly from primary partitions. Your Vista is in sda5 and its boot files are in the XP install in sda1.
       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by juanma21a on 2013-12-28
Oh, thanks you!

But, I don't understand what can I do for fix my problem?

Sorry, I am a little newbie.

---

### Post by oldfred on 2013-12-28
Grub only boots a working Windows. If you install Windows boot loader with Boot-Repair or from a Windows XP or Vista repairCD can you directly boot Windows? 

If not, you may then need to repair your Windows and probably should use a Vista repairCD as Vista has taken over the boot of XP. Often chkdsk which cannot be run from Linux may be required.

---

