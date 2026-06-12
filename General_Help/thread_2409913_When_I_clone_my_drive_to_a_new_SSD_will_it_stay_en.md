---
title: "When I clone my drive to a new SSD will it stay encrypted? Which software to use?"
date: 2019-01-08
forum: General Help
---

### Post by blackbird34 on 2019-01-08
Hi everyone. 

I've had a crucial SSD in my laptop running KDE Neon (currently 18.04 based on Ubuntu Bionic) for a while, with an encrypted /home partition. It has 417 bad sectors and I've bought a new SSD to replace it. I want to clone the system over and I have some questions: 

* What software/ command line would you recommend for the cloning? 

* /home is currently encrypted but would I be able to have it unencrypted on the new drive? Would be useful to avoid data loss if the motherboard dies (4.5 year old laptop). 
 
Thanks

---

### Post by oldfred on 2019-01-08
I do not really know encryption.
But I almost always suggest a new install as the easier way to add Ubuntu to a new drive. You then still have old drive (if it is still working).
And once you have new install, you restore all your data from your backup, use list of installed apps to reinstall all your apps and perhaps some settings from /etc if you made system setting changed. Only if you installed Server type software may you have folders in your / that also need to be copied, but you are backing those up anyway.
Becomes a good test that backup restores system completely, and you still have old drive as functional system.
If you do any sort of image, copy, you cannot reboot with both drives connected as duplicate UUIDs are not allowed.

Is your install in UEFI boot mode? You then also cannot copy partitions, as gpt as GUIDs in partition, partition table & backup partition table that must remain in sync. May be possible to fix, but again, new install is quicker & easier. You can image copy entire drive as then partitions tables also are copied. But if using dd (nickname Data Destroyer) it must be same size drive to same size drive.

I just did a new install to my sdb drive. I already had ISO downloaded, / partition created on drive and then loaded ISO into RAM (toram parameter) and installed in about 10 minutes. Another 15 to 20 to update & some time to manually reconfigure as I do not restore /home as testing something different. But my full install to a flash drive was over an hour, SSD & RAM make it really quick to install.

Whenever you boot into your system, you are decrypting the data. I would then think you could copy that and not copy the (hidden) encrypted folder where data is saved when you shutdown. If you image copy there would have to be some settings to change to remove the encrypted folder & the request to decrypt it when booting.

---

### Post by Kris_M on 2019-01-08
When I am moving to a new SSD, I try to have 2 or 3 things that I think will work - all on bootable USB flash thumb drives (that I have tested to make sure they boot on my current BIOS(things change and UEFI screws everything up - I am on BIOS/MBR).  If I were doing it today, I would give Macrium first chance since I use that to back up my SSD, and have used it successfully a few times to restore everything, and of course I would also back it up to HD first, just to have a copy - can't be too careful(I have 2 HD drives that I can connect to my laptop if needed for such.) .  Others I have in the little thumb drive box are an EaseUs Partition Master 10.5 but I can't recall how good it is with Linux and Grub, and at the moment would tend to trust it less.  Of course I always have sticks for gparted and rescatux and clonezilla. Having said that, I guess I would also first use clonezlla to do a full copy of that SSD to a ext4 work partition, just to be on the safe side. But in all likelihood Macrium will make it a piece of cake . Do remember that if you have a windows partition on that SSD as I do (win7 and ex-win10) you will probably have to re-activate them. That's why I bought a cheap full retail license for win7 (and actually win10 though I have erased win10 but grub still sees it as win10 though if you boot to it it will error out).

I use win7 at the moment for my old games because, though I had them when I was on 18.04, I got lazy and when I installed 18.10 clean, I didn't bother to install wine and them on it. I don't seem to play them these days anyway.  Likely a couple months after 19.04 is out I will do the same thing, again, to a separate partition (the one 18.04 is in).

I know nothing about encryption and whether that would affect things.

---

