---
title: "fidk boot flag and grub"
date: 2007-06-22
forum: General Help
---

### Post by SteveF on 2007-06-22
Currently, grub is installed on my first hard drive.  It reads the menu list from the second hard drive partition 6 which has Kubuntu installed on it.  I have Ubuntu installed on partition 7.  I'd like to change grub to read from the Ubuntu menu list on partition 7.  If I change the boot flag for the second drive using fdisk to be partition 7, will grub read from that menu list?

All the help I've seen involving grub and changing partitions seems to imply reinstalling grub and I don't want my menus modified so I thought just changing the boot flag might do it.

Thanks,

Steve

---

### Post by 5-HT on 2007-06-22
I doubt it, Linux doesn't really care about boot flags. You can easily boot from a partition without them.

What I like to do is have a separate /boot partition and make sure my menu.lst there is in order. You can take a look at grub's documentation, there may be something there.

Here's a dirty, dirty little hack that might work:
Copy all pertinent menu.lst entries from partition 6 over to the one in partition 7.
Then symlink partition six's menu.lst to your menu.lst on parition 7.
Any time grub will be looking at /boot/menu.lst on parition 6, it'll read from your menu.lst on parition 7. Debian's automagic grub updates script can still do its magic.

Hopefully someone more versed in the ins and outs of grub will come along.
cheers,

---

### Post by SteveF on 2007-06-22
I ended up running:
sudo grub-install --root-directory=/boot /dev/hda
while I was logged into Ubuntu.

That solved it.  I thought I was going to have use the install disk, but those messages might have been related to not being able to boot into a valid partition.

So I'm all set.

Steve

---

