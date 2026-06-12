---
title: "Migrating a dual boot from an HDD to an SSD - anything specific to know?"
date: 2023-02-11
forum: General Help
---

### Post by JustSomeCanuck on 2023-02-11
Hello everyone!

I have a desktop computer with a dual boot of Windows 10 and Ubuntu 22.04, both installed on a 1 TB HDD. If I wanted to migrate one or both OSes onto a new SSD, what is the best way to go about doing that? Are there any possible obstacles or concerns I need to know about?

Ubuntu boots significantly faster than Windows at the moment, so moving that is optional at this point.

---

### Post by dragonfly41 on 2023-02-11
I have several external SSD's.
The only tip to pass on is ensure that you first use GParted to create a first partition, fat32, label ESP, size 500MiB, flags: boot, esp
This ensures that you don't need the EFI partition in the harddrive. except for Windoews.
I have also installed reFind in there (alongside standard Grub) but that is optional. I just prefer it for custom boot menu.

The other point to consider is swaping your internal HDD for SSD and use the HDD for backups.

I use Startech dual docking bay which requires USB 3 for performance. USB 2 is too slow to run Ubuntu.

So to summarise.
Internal:
Windows on SSD (changed HDD)
External:
StarTech dual docking bay, with two SSD in hot pluggable caddies EZConvert IcyDock

---

### Post by mIk3_08 on 2023-02-12
> **JustSomeCanuck said:**
> Hello everyone!

I have a desktop computer with a dual boot of Windows 10 and Ubuntu 22.04, both installed on a 1 TB HDD. If I wanted to migrate one or both OSes onto a new SSD, what is the best way to go about doing that? Are there any possible obstacles or concerns I need to know about?

Ubuntu boots significantly faster than Windows at the moment, so moving that is optional at this point.
In my case, I use clonezilla for cloning the disk. since you have a  large size of hdd which is 1TB and you haven't mention yet the size of  your ssd. mostly cloning in clonezilla, As far as I know. It is  recommended that you use larger destination disk than the source disk. I  haven't tested it yet but you can try the partition cloning. Cloning  only part of your 1TB disk. Just be sure that the data you clone from the  source disk is right fit to the size of destination storage. I'm not an expert of this but hope you get some of this tip. Regards  and cheers.

---

### Post by ActionParsnip on 2023-02-12
I'd run a final full backup and then switch. You can restore data from the backup as you need.
You may want to plan your file systems if you go down this route rather than slamming next in the Windows installer and using all of the available disk (this is the default in Windows). You then won't have to resize the disk to install Ubuntu. You could even have a partition purely for your casual user data.

---

### Post by JustSomeCanuck on 2023-02-12
I also found this helpful page on my own:

[https://askubuntu.com/questions/1403444/how-can-i-clone-a-dual-boot-with-windows-10-and-linux](https://askubuntu.com/questions/1403444/how-can-i-clone-a-dual-boot-with-windows-10-and-linux)

So, if I understand the replies and the above answers correctly, here's exactly what I should do:

1) Make a backup.
2) Clone the Windows 10 partition using the software provided with the SSD.
3) Using a live USB, clone the Ubuntu partition to the SSD with Gparted (if needed - Ubuntu runs significantly faster off of the HDD than Windows and I'm not surprised).

I expect the SSD will be 1 TB to keep things simple.

---

### Post by oldfred on 2023-02-12
Note that if cloning, you cannot have duplicate UUIDs and GUIDs when rebooting.
So old drive has to be removed or you have to edit all partitions to have new UUIDs & GUIDs. And if you want to boot old install of Ubuntu have to edit fstab & reinstall grub, so it knows to boot from new UUIDs.

With Ubuntu often better to just do new install & restore from backup.

---

### Post by JustSomeCanuck on 2023-02-15
Well, the cloning seemed to work, but after that I ran into some issues with grub, so I just decided to reinstall Ubuntu on the SSD. Since I had all my data backed up, it wasn't a big deal.

---

