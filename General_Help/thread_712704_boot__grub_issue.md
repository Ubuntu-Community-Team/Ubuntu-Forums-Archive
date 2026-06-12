---
title: "boot / grub issue"
date: 2008-03-02
forum: General Help
---

### Post by anystupidname on 2008-03-02
Problem: it won't boot. At first it gave either grub error 15 or 17 but as I've attempted different maneuvers to rescue it, it has gotten to the point where I just get a blank screen and blinking cursor

The system consists of a stinkpad T30 with single HDD:
(hd0) /dev/sda (internal IDE)
(hd0,0) /dev/sda1 = swap 512MB
(hd0,1) /dev/sda2 = NTFS (XP) 5GB
(hd0,2) /dev/sda3 = EXT3 (linux mint) 8GB (active)
(hd0,3) /dev/sda4 = EXT2 (data partition I must not lose) 5GB

It all started because I had to install XP. So I re-arranged partitions to squeeze in the elephant.

What is most frustrating about this situation is that I had it working fine immediately after manually reinstalling grub from a Kubuntu liveCD (after the elephant clobbered my MBR). Then I popped back into XP to do a firmware update on a integrated wireless NIC and install SP3, and when I rebooted, grub gave me the errors.

Things I've tried:
supergrubdisk
grub-install /dev/sda
grub
find /boot/grub/stage1 (this didn't give an error originally but is throwing error 15 or 17 now)
root (hd0,2)
setup (hd0) (this now throws an error about can't find partition or not valid block device)

I really don't want to reinstall linux Mint as I have been running it for a while and got it all tweaked out the way I like. Please help! Any assistance would be greatly appreciated! Thanks.

---

### Post by fyrmedic on 2008-03-02
I could be wrong, but I think you will have to do a re-install so that grub is in charge of your mbr. I have had similiar problems with Microsoft products screwing it all up.

You may be able to work around the reinstall issue a little bit by backing up your home directory, doing a fresh install, then copying your /home from the back-up.  That will preserve a lot of the settings that you have already set up. You will just have to spend some time re-installing the packages that you use.

When you do the re-install the installer should give you the opportunity to manually set up your partitions manually and you can tell it not to format your data partition. I would highly recommend splitting your / drive into / and /home so that you don't have to worry about it in the future if you have to re-install again.

Good Luck.

---

### Post by anystupidname on 2008-06-20
I deleted the swap partition and recreated it using a gparted livecd and repeated the grub, find, root, setup steps and that did it?!? Keeping my fingers crossed...

---

