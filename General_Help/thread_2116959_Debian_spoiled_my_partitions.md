---
title: "Debian spoiled my partitions"
date: 2013-02-17
forum: General Help
---

### Post by Carllacan on 2013-02-17
Hi!

I've just installed Debian Squeeze along with Ubuntu 12.04 and I'm already having problems...

Ubuntu won't start. While booting, it eventually stops and tells me that it is unable to mount /tmp. Same thing happens with the rest of partitions, except /home and / (which were not used on Debian installation). I checked Debian's fstab and it turns out that the UUID of the devices differ from those on Ubuntu's fstab. 

Has Debian changed my devices UUID? Can I just edit Ubuntu's fstab so the UUIDs are those on Debian's fstab?

Thank you for your time.

---

### Post by The Cog on 2013-02-17
Yes, I think that Debian probably reformatted the partitions which would have changed their UUID. If that's the case, anything that was on them is gone.

Yes, you should be able to use a live CD (or Debian) to edit and correct /etc/fstab on the Ubuntu root partition.

You will be dependent on Debian's installation of GRUB. If you want to revert to Ubuntu's GRUB, the two commands in Ubuntu are:
```
sudo update-grub
sudo grub-install /dev/sda
```
but I would probably leave Debian's GRUB on there unless there is a reason to change again.

---

### Post by Carllacan on 2013-02-17
> **The Cog said:**
> Yes, you should be able to use a live CD (or Debian) to edit and correct /etc/fstab on the Ubuntu root partition.

Ok, just to be sure: it is safe to rewrite ubuntu's fstab UUIDs to the ones on Debian, right?

Thank you very much.

---

### Post by The Cog on 2013-02-17
> Ok, just to be sure: it is safe to rewrite ubuntu's fstab UUIDs to the ones on Debian, right?
Not sure what that means. So here's the procedure I would use. It assumes that I know exactly what is on which partition already:

Boot Debian or a live CD
Use **sudo blkid** to get the current UUID of all partitions
Mount the Ubuntu root partition at /mnt : **sudo mount /dev/sdaX /mnt**
Edit /mnt/etc/fstab and edit it : **sudo nano /mnt/etc/fstab**
Correct the UUIDs, save and reboot

Out of interest, you could compare the Debian fstab with the blkid output, but I expect that they match so no surprises.

---

### Post by Carllacan on 2013-02-18
> **The Cog said:**
> Not sure what that means. So here's the procedure I would use. It assumes that I know exactly what is on which partition already:

Boot Debian or a live CD
Use **sudo blkid** to get the current UUID of all partitions
Mount the Ubuntu root partition at /mnt : **sudo mount /dev/sdaX /mnt**
Edit /mnt/etc/fstab and edit it : **sudo nano /mnt/etc/fstab**
Correct the UUIDs, save and reboot

Out of interest, you could compare the Debian fstab with the blkid output, but I expect that they match so no surprises.


Thanks, worked like a charm!

---

### Post by Carllacan on 2013-02-18
> **The Cog said:**
> Not sure what that means. So here's the procedure I would use. It assumes that I know exactly what is on which partition already:

Boot Debian or a live CD
Use **sudo blkid** to get the current UUID of all partitions
Mount the Ubuntu root partition at /mnt : **sudo mount /dev/sdaX /mnt**
Edit /mnt/etc/fstab and edit it : **sudo nano /mnt/etc/fstab**
Correct the UUIDs, save and reboot

Out of interest, you could compare the Debian fstab with the blkid output, but I expect that they match so no surprises.

Thanks, worked like a charm!

---

### Post by The Cog on 2013-02-18
Oh good.

You can mark the thread solved using the Thread Tools pull-down at the top.

---

### Post by Carllacan on 2013-02-18
> **The Cog said:**
> Oh good.

You can mark the thread solved using the Thread Tools pull-down at the top.


Thanks again, I didn't know how to do it xD

---

