---
title: "Boot Error/Grub Problems"
date: 2016-11-28
forum: General Help
---

### Post by laminar-boh on 2016-11-28
Hello,

I tried to boot my laptop up, running the latest version of Ubuntu, and got the "Fix Minimal BASH like line editing..." error (described here: [https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/](https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/)). I tried booting to a live USB with Ubuntu and running boot-repair, as described. When I run boot-repair, it gets stuck on "Purge and reinstall the GRUB of: sdb2 (upd)". It says to wait for several minutes, but I have let it run for several hours and nothing happened. I have tried reinstalling the GRUB via the command line, but have run into a whole other host of errors. 

Here is the info script produce by Boot Repair: [http://paste2.org/OYbpELPZ](http://paste2.org/OYbpELPZ)

I don't know if the errors are because there are EFI partitions on both sda1 and sdb1, but Linux is on the sdb2 partition. A

Any help would be gratefully appreciated. I'm really confused at this point and am just looking to be able to boot back into my OS so I can get at some important files. I am not the most versed person in Linux, so please give any advice in as straightforward a manner as possible

---

### Post by yancek on 2016-11-28
Your output shows EFI partitions on both drives.  Problem is that boot repair generally shows in it's output the names of the EFI files and nothing shows in your output.  There is also no grub.cfg file  for either drive, sda or sdb.  If this is a new install, it doesn't look like it completed successfully.

---

### Post by gordintoronto on 2016-11-29
Does "Purge and reinstall the GRUB of: sdb2 (upd)" mean that you put grub on SDB2? That's not an appropriate location.

---

### Post by oldfred on 2016-11-29
With UEFI grub always installs to the ESP - efi system partition on sda.
But script did not show any .efi boot files or /EFI/ubuntu folder in sda1.

Was this a RAID configuration or Intel SRT or similar cache that looks like RAID from Linux?
Grub does not correctly install to RAID from desktop.

If you are not using Intel SRT nor RAID.
 > Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb 

Then reinstall grub.

---

