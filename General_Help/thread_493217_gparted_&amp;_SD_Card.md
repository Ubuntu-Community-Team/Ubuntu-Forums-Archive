---
title: "gparted &amp; SD Card"
date: 2007-07-05
forum: General Help
---

### Post by johnaaronrose on 2007-07-05
I want to clear existing partition (taking all of storage) & create new ones on a new SD card. Using gparted, it shows a padlock icon by the card's device name. All activities such as Delete Partition are grayed out . The device is shown as /dev/sda2.

I've tried to run gparted from (Gnome) Terminal as root, but that gives same 'lock'. I've looked at the documentation for the meaning & howto clear the padlock icon, but no success. 

Help!!!

---

### Post by az on 2007-07-05
I'm not sure if you are able to partition a memory card.  It's not like a hard drive in that it has a partition table....

---

### Post by stchman on 2007-07-05
> **az said:**
> I'm not sure if you are able to partition a memory card.  It's not like a hard drive in that it has a partition table....

You can partition a USB flash drive using gparted.  I figure that and a memory card are practically the same.

---

### Post by johnaaronrose on 2007-07-06
I must have been asleep when I posted yesterday! The device I referred to is the Linux swap partition, which of course explains why it is locked.

However, why is gparted not displaying a line for my Kingston 2gb sd card? Nautilus can see the card and allows files to be copied to it. What device should an sd card be shown as (i.e. /dev/?)?

---

### Post by linuxeventually on 2008-03-24
Hopefully this well help out any other people googling for answers on forums that have questions but seem to have no answers (and yet still come up as the top results in query). Oh and please don't reply to a post with a "I don't know". Thank you. Your answer is of course **/dev/mmcblk0p1** should be the entry for an SD card. If there is a lock icon, attempt to unmount the partition with umount.

---

