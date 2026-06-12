---
title: "Can't boot into Windows after my dad removed Ubuntu"
date: 2012-11-28
forum: General Help
---

### Post by sogeking99 on 2012-11-28
I gave him my old laptop which had Ubuntu 12.04 dual booted with Windows 7. He went to Windows recovery and chose whole hard drive, now when he boots he gets this error:

error no such partition grub rescue

I am guessing it's because it was going to the ubuntu bootloader, but how do I fix this so he can access Windows again?

---

### Post by elliotn on 2012-11-28
get a windows 7 CD and repair bootloader

---

### Post by sogeking99 on 2012-11-28
I don't have a CD, it was just the one that came with the laptop.

---

### Post by haqking on 2012-11-28
Get a Disk from a friend if not then download Easy BCD or similar (it has option to repair MBR) [http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/)

or partition wizard [http://www.partitionwizard.com/partition-wizard-bootable-cd.html](http://www.partitionwizard.com/partition-wizard-bootable-cd.html)

---

### Post by slickymaster on 2012-11-28
Take a look at this, [Restore the Windows bootloader to MBR after dual-booting with Linux]("http://www.linuxbsdos.com/2012/03/10/restore-the-windows-bootloader-to-mbr-after-dual-booting-with-linux/"). I think it's exactly waht you need.

---

### Post by Mark Phelps on 2012-11-28
Go to the partition Wizard site mentioned in the previous link, download the Boot CD (to a Windows PC), and burn the CD.

When you boot from that CD, it will have the option to Repair the MBR -- choose that, and it will replace the Linux MBR with a Windows MBR.

After that, you should be able to boot into Win7 OK.

---

### Post by coffeecat on 2012-11-28
@sogeking99, nothing that much to add to the excellent suggestions you have received already, except to say there's a community documentation page specifically about this here:

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

You'll see that you can use an Ubuntu live CD to do the job so long as the Windows partition boot sector is healthy.

---

