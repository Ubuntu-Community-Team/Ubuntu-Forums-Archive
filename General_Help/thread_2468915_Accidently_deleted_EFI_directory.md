---
title: "Accidently deleted EFI directory"
date: 2021-11-14
forum: General Help
---

### Post by trash1464 on 2021-11-14
I cant believe I actually did this but I accidentally deleted  the 538MB FAT32 partition of my main Ububtu 20.04 hard drive. I believe that to be the EFI partition. The PC is still running but if it ever shuts down it is doubtful that it will reboot without that partition. Is there a way to recover?

---

### Post by oldfred on 2021-11-14
If not rebooted recover partition:
[http://ubuntuforums.org/showpost.php?p=10364557&postcount=34](http://ubuntuforums.org/showpost.php?p=10364557&postcount=34)

At minimum backup partition table and save to another device.
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors (if sda or whichever device it is):
sudo parted /dev/sda unit s print

If you have to recreate ESP - efi system partition it will change GUID/UUIDs, so restoring from backup probably will not work.
Just make sure you have working repair flash drives for current versions of all installed systems or other bootable device to be able to reinstall boot loaders.
You typically just need to totally reinstall grub-efi-amd64.

---

### Post by Impavidus on 2021-11-14
Recreate that partition, with the EFI flag. It will get a new UUID, so I think you have to edit /etc/fstab to match. Mount it and reinstall grub:```
sudo grub-install /dev/sda
```or whatever your drive is called.

I may have missed something, so wait a bit before rebooting. Someone else may have some more comments.

If something goes wrong, make sure you've got a live disk. This should be easy to fix with one of those.

Edit: oldfred above is the specialist on this. Try that.

---

### Post by hk42 on 2021-11-14
A tip to avoid accidental deleting of partitions is to give them a useful name or label.
I recently discovered that /etc/fstab allows to use Label to mount partitions.
This too can be very useful.
For example my /home is on a SDcard I can move it between PC's.

---

### Post by trash1464 on 2021-11-15
Fixed!
Since the system was not rebooted, I had a fully functional system to work with. 
Using Disks GUI the EFI partition was recreated with Mount Point /boot/efi and formatted FAT32. 
Mounted the new EFI partition
FSTAB was edited to change the UUID to the newly created UUID. 
Installed GRUB into the new efi partition
Held breath and rebooted
Success!

I will NOT repeat the mistake of deleting EFI partition again!

---

