---
title: "Is there a way to have a multicomputer linux  usb?"
date: 2013-02-13
forum: General Help
---

### Post by mufflen on 2013-02-13
I'm looking for a way to have a bootable USB that launches Linux and has all my files and programs like it was when i used it on the last computer.

I have run into a few problems just installing Linux on a 
pen-drive. 
Like Hangs up at a purple screen after launching on a different computer. 
Or goes to a black screen and says:

mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init= bootarg

---

### Post by C.S.Cameron on 2013-02-13
Unless you have installed proprietary drivers, a Persistent or a Full install flash drive should work on any computer unless it is too old, (<1GB RAM), or too new, (UEFI).

Try UNetbootin or Startup Disk Creator for a Persistent install, or do a Full install to the flash drive.

If you do a Full install, unplug the internal drive or at least confirm that you are installing grub to the root of the flash drive.

---

### Post by sudodus on 2013-02-13
> **C.S.Cameron said:**
> Unless you have installed proprietary drivers, a Persistent or a Full install flash drive should work on any computer unless it is too old, (<1GB RAM), or too new, (UEFI).

Try UNetbootin or Startup Disk Creator for a Persistent install, or do a Full install to the flash drive.

If you do a Full install, unplug the internal drive or at least confirm that you are installing grub to the root of the flash drive.
+1
I have such an installed USB system, and it works well. The main disadvantage compared to an internal drive is that it is slow when there are many updates, and many small files need to be written.

I suggest that you get a fast USB pendrive, if possible with USB 3. Even in a USB 2 port it will be faster, because often the flash is slower than USB 2, so the flash will limit the speed with standard USB 2 pendrives.

---

### Post by LiamOS on 2013-02-13
[I did this]("http://forums.gentoo.org/viewtopic-t-944994.html") with Gentoo linux, and it works great.
I've also done something similar with linux mint, installing to a USB drive, but it was very unstable due to lack of swap space on a lot of machines.

A few key things are filesystem choice, and how you're mounting everything.
ReiserFS is pretty good for USB drives, but it'll take a really long time to write a lot of small files(untarring kernel sources, etc.). btrfs is also fantastic if you know how to use it well, but the real performance comes from using squashfs and mounting everything in tmpfs.
I'm not sure how easy it is to customise an ubuntu installation to that degree, and it'd help to have a lighter system in terms of load times, so I'd recommend something like Arch/Gentoo(maybe Debian) if you want as much performance as you can get, since you can keep everything stripped back where possible.

---

### Post by kurt18947 on 2013-02-13
> **sudodus said:**
> +1
I have such an installed USB system, and it works well. The main disadvantage compared to an internal drive is that it is slow when there are many updates, and many small files need to be written.

I suggest that you get a fast USB pendrive, if possible with USB 3. Even in a USB 2 port it will be faster, because often the flash is slower than USB 2, so the flash will limit the speed with standard USB 2 pendrives.

Absolutely.  I'm using Sandisk Cruzer blades for tinkering with 13.04.  I did a full install IOW delete and recreate partition, format to ext2 (better for flash I think.  No journal so fewer writes.  It's possible to disable journaling on ext4 but I don't know how to do that),  use the 'something else' option on the installer.  Make **sure **I'm writing to sda2 or whatever and make sure GRUB gets installed on the correct drive.  By default it's not.  Everything works quite well but for updates, I start the process, make sure it's running then go do something else for a while, it's slow.  As is typical with flash drives, read speed is pretty good, write speed sucks.  I haven't tried a USB3 yet, that's on the list.  The other question is durability but I'm not using this install for anything of consequence.  If the drive craps the bed, I'm out $5.

The benefit of a 'real' install vs. a persistent install is that updating won't break a 'real' install,  updating may break a live USB w/persistence.

---

