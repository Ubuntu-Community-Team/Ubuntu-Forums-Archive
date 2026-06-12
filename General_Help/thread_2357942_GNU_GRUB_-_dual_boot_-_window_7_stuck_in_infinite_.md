---
title: "GNU GRUB - dual boot - window 7 stuck in infinite loop after update (need fix)"
date: 2017-04-07
forum: General Help
---

### Post by topherx on 2017-04-07
I am running Gnu grub version 1.99-21ubuntu3.19 with Ubuntu & Window 7 partitions.

Windows 7 worked fine until a recent update, when Windows starts boot process and gets stuck in infinite loop with message: "Failure configuring windows updates reverting changes. Do not turn off computer". This Windows message stays on screen for 10 hour and more.  

How can I repair Windows 7.  I'm not able get a previous restore point or boot in safe mode.  I considered booting from the my windows 7 DVD to repair windows but fear that this will blow out GNU Grub and Ubuntu partition. I'd like to repair windows 7 (and keep my applications) versus blowing away the partition and reinstalling from scratch.

Any suggestions are welcome.

Thanks,
topherx

---

### Post by oldfred on 2017-04-07
Repairing Windows will normally reinstall the Windows boot loader. 
So you need your Ubuntu live installer to restore grub afterwards. 
Some major Windows updates like a reinstall or update from Windows 7 to Windows 10 has caused issues as it does not write a logical Linux partition back to partition table.
So always best to have good backups. And know configuration. Often best or easiest to run Boot-Repair and save a copy of its boot configuration report as part of normal backup.

You may be able to temporarily restore the Windows boot loader and then with f8 get into its repair console. The with Ubuntu live installer add Boot-Repair and restore grub to MBR, or manually restore grub.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[URL="https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader"]https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader
[/URL]
 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by topherx on 2017-04-24
Thanks for your suggestions, oldfred. Fortunately, my windows 7 upgrade issue resolved itself.  What kind of backup do  you recommend that will include the GNU GRUB boot loader along with the Ubuntu & Win 7 partitions?

---

### Post by oldfred on 2017-04-24
It is easy to reinstall grub to MBR, so we normally do not back that up.

Link above has instructions on restoring MBR with BIOS based systems.
But you do need to have Windows repairCD or flash drive and the Ubuntu live installer so you can do those repairs.

---

