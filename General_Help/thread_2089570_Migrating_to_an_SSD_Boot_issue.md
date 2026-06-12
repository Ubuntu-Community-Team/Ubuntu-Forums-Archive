---
title: "Migrating to an SSD: Boot issue"
date: 2012-11-29
forum: General Help
---

### Post by fmmarzoa on 2012-11-29
Hi there,

I am trying to migrate to a new SSD, but keep my old HDD still on the system for backups and so.

I have used Clonezilla to save and restore the partition from the old HDD to the new SSD, and this step works fine.

Now, the problem I have is that I am not being able to install grub2 so it boots fully from the SSD. It seems like it is succesfully installed on the MBR of the SSD, since if I select this device as boot device from BIOS it starts to boot the system, but as soon as it starts it does it from the old HDD.

It seems like it were swaping the disks: so, before the HDD was /dev/sda, so I installed grub for starting from /dev/sdb, that was the SSD. But now it seems like /dev/sdb is the HDD instead... O_o it seems like those devices /dev/sd* are created after booting, so I should use devices UUID instead on fstab, but I have no idea on how to find them to start...

Well, ANY HELP IS WELCOME.

Thanks a lot in advance,

---

### Post by oldfred on 2012-11-29
You probably have duplicate UUIDs.

Post this & use code tags to preserve formatting.

       sudo parted /dev/sda unit s print
            cat /etc/fstab


       
 Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid

---

