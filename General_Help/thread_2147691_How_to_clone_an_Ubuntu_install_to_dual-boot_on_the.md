---
title: "How to clone an Ubuntu install to dual-boot on the same system?"
date: 2013-05-22
forum: General Help
---

### Post by roots on 2013-05-22
Hi all,

I have the following disk setup:

sda: SSD
sda1: nfts (boot)
sda2: nfts (Windows 7)
sda5: linux swap
sda6: ext4 (/home)
sda7: ext4 (/ (Ubuntu 12.04.2 AMD64), primary OS)

sdb: HDD
sdb1: ext3 (data)
sdb2: ext3 (data)

sdc: HDD
sdc1: ntfs (boot)
sdc2: (unknown)
sdc3: ext3 (old Ubuntu install)
sdc5: ext3 (EMPTY)
sdc6: ext3 (data)
sdc7: ntfs (data)

GRUB2 is sitting on sda, I'm using Ubuntu 12.04.2 about 99% of the time. Now, I want to toy around with different packages etc. in the near future and I don't want to mess up my primary OS (Ubuntu install). Therefore I want an exact clone of my Ubuntu install (both / and /home) on one of my HDDs, where I can boot into besides my "normal" OS. I don't want both OSes to share any data on the disks. sdc5 seems just fine to host this sandbox, as it has plenty of space.

Which would be the best way & tool to achieve this without messing with my current Ubuntu install? How do I make sure to keep GRUB where it is (sda) and have it recognise the cloned Ubuntu install on sdc5 as another bootable OS?


Any help very much appreciated!
r.

---

### Post by HiImTye on 2013-05-22
why not use virtualbox?
you could also make a chroot jail to play around in, or you could use rsync, or some other backup tool
if you want an identical partition you could even dd

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by roots on 2013-05-22
VBox is not an option, as it does not reflect my real hardware (video card etc.). I've not used chroot before, but it seems to me, that this is rather a command line thing and not a "complete OS" with all desktop fancy etc.?!

As far as dd and backup tools are concerned, I'm not quite sure how they would handle the MBR / grub thing. If I only clone / and /home into two appropriate partitions on the second drive, I assume it would leave MBR / grub unaffected? Therefore, after cloning the partitions, I would just have to update-grub in my primary OS and at the next reboot I should be able to boot into the clone as well? And: What would happen with the UUIDs, would they be cloned as well?


r.

---

### Post by HiImTye on 2013-05-22
chroot is command line, you could use it to create a virtual environment so you can reuse your exidting file systems. likely this is outside your technical proficiency, you'd want to do it in virtualbox abfew times at the very least to get the feel for it (maybe use the Arch installer)
you could use rsync in archive mode, or just do a direct cp, each has their drawbacks. rsync has a switch to preserve file ownership, which might be easier to run as root (to copy inaccessible files). I'm not sure of the best method, I'm just trying to give you some ideas.
dd is a direct copy, it doesn't care about file systems, you use it to copy directly, but it comes with the danger that if you use it incorrectly, you could lose oyher data (copying over other partitions, etc)
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

