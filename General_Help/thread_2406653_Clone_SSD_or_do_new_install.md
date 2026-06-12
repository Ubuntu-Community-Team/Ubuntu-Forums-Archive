---
title: "Clone SSD or do new install?"
date: 2018-11-23
forum: General Help
---

### Post by Odyssey1942 on 2018-11-23
Not sure whether this is primarily software or hardware, so if it needs moving, please suggest where.

I recently installed Ubuntu MATE 18.04.1 onto an older 120GB SSD and it boots up and generally works OK. As this computer is intended to be my new workhorse until at least Ubuntu 20.04, I have a new 250GB SATA that I want to clone the existing SSD UM install to and use it in this computer.

I have done a modest amount of personalization of the existing SSD UM install, and the install works, hence the interest in cloning.

Having said that, it will probably take less time to just install UM onto to the new SSD than to learn how to clone the old one to the new.

Your thoughts and guidance welcomed. If to clone, which software do you recommend? (I think I remember reading that someone reccommeded Macrium).

If to do a new install, and in either case, does the fact that this is a dual boot (UM on the SSD and Win 10 on the original HDD) dictate any special step/s?

---

### Post by oldfred on 2018-11-23
While you can clone, new UEFI with gpt requires you to clone an entire drive, not a partition as each gpt partition has a GUID that must match the primary partition table and the backup partition table.

Often easier to just do a new install than try to edit/fix cloned install. Your backup procedures should be backing up everything you need for when you drive fails or system breaks, anyway.

You can do a new install and copy /home. That has all your user settings and data (unless using a separate data partition also). Only if you have server apps may you have them in / and would need to copy them also, but permissions & ownership then are more important also.

If you manually edited some system files like grub settings or NFS or Samba may you want to back up /etc. New install unless same version may not need all the same settings in /etc. I only edit a couple of files, and copy those to my /home so my backup of /home includes those.

You also can export a list of installed apps and the use that to easily reinstall all of them.

Since you have old drive, this is an ideal time to test that your backup procedures, backup everything you need. You use backup to restore to new drive, and then if anything missing, you still have old drive to go back to (and update backup procedure).

If multiple drives, best to disconnect other drives when installing. Then you can plug in other drives and copy data & update grub to boot Windows. Be sure to install in same boot mode as Windows is installed, either UEFI or BIOS/CSM/Legacy. How you boot install media UEFI or BIOS is then how it installs.

Note that SATA port you plug drives into will probably be the drive order. Or SATA0 will be sda, SATA1 sdb etc. Its just with my system my flash drive becomes sda and every other drive moves up one. Ubuntu's grub in UEFI mode wants to install to first drive or sda or if NVMe first drive. That is why often best to disconnect other drives, so new drive will be sda, no matter what port it is plugged into.

---

### Post by Odyssey1942 on 2018-11-24
A new install on the new SSD is almost certainly safer for me. Should I disconnect the HDD when doing the install (not sure quite how the dual boot gets set up)? Thanks.

---

### Post by oldfred on 2018-11-24
Best to disconnect drive. Many newer systems have a setting in UEFI to turn on/off a drive, so you do not even have to open case.

Just be sure to boot in same boot mode as Windows is installs, either BIOS or UEFI.

---

