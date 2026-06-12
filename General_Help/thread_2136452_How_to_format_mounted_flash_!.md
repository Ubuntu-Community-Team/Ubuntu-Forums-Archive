---
title: "How to format mounted flash ?!"
date: 2013-04-17
forum: General Help
---

### Post by redred1 on 2013-04-17
Hi,
i mount ubuntu iso to my flash memory, it's separated to 2 drive, now i want format it and merge it to 1 drive, how can i done it ?!
Thanks in advance .

---

### Post by ajgreeny on 2013-04-17
> **redred1 said:**
> Hi,
i mount ubuntu iso to my flash memory, it's separated to 2 drive, now i want format it and merge it to 1 drive, how can i done it ?!
Thanks in advance .

I don't understand your question, I'm afraid, so tell us more about your situation.

Do you have a live USB (flash drive) and is that what you mean by "I mount ubuntu iso to my flash memory"?

---

### Post by cody1233 on 2013-04-17
From what I understand, you need to install gparted, unmount the device, create a partition table, and write it to the USB drive.  If this is not right please post!

---

### Post by redred1 on 2013-04-18
I use [FONT=Ubuntu Mono]dd if=ubuntu.iso of=/dev/sdc5
and mount iso to use flash !
now i want format it ![/FONT]

---

### Post by fantab on 2013-04-18
What you are saying is that you have two partitons on the USB Drive after burning Ubuntu on it, right?

Follow the commands below... but** make ablsolutely sure the the device name of your USB Drive**. If you make a mistake with this there could be serious consequences. UNMOUNT THE DIRVE FIRST.

```
sudo dd count=1 bs=512 if=/dev/zero of=/dev/sd**x**
```   ('**x**' is your USB Drive number not partiton no.)

Now you can use either **Gparted** or **Disks** to create a new partitions table MSDOS  and format it with either FAT or Ext4. OR you can also use '**cfdisk**':

to format it to FAT:
```
sudo cfdisk /dev/sdx
sudo mkfs.vfat -F32 /dev/sdx1
sudo dosfslabel /dev/sdx drivelabel
```

---

