---
title: "Copying my Ubuntu partition, will it work?"
date: 2007-07-07
forum: General Help
---

### Post by timo1023 on 2007-07-07
I'm going to backup my Ubuntu partition (only a few gigs), wipe my HD, and then copy it back over, at least that's the plan. My ubuntu partition is /dev/hda6, though, and when I copy it over as the only partition, won't it become hda1 or something, and not be able to mount the filesystem? How can I work this out?

Thanks.

---

### Post by kagashe on 2007-07-07
Yes if you make only one partition it will become hda1. But hda1 or hda6 is immaterial because if you reformat the disc and simply copy the partition you can't boot into Ubuntu since the boot sector would be wiped out too.

You will have reinstall Grub on MBR and when you do that it will rewrite the menu.lst file in /boot/grub

kagashe

---

### Post by timo1023 on 2007-07-07
Sorry I'm a noob; what's MBR, and how would I go about installing Grub on it? (I know what Grub is, at least, heh.)

Thanks.

---

### Post by Gremlinzzz on 2007-07-07
MBR=master boot record

---

### Post by kagashe on 2007-07-07
> **timo1023 said:**
> Sorry I'm a noob; what's MBR, and how would I go about installing Grub on it? (I know what Grub is, at least, heh.)

Thanks.MBR fom Wikipedia:
> A Master Boot Record (MBR), or partition sector, is the 512-byte boot sector that is the first sector ("Sector 0") of a partitioned data storage device such as a hard disk.
When you installed Ubuntu the stage 1 of Grub was written on the MBR and stage 2 on hda6 in /boot/grub/menu.lst file.

When you reformat the disc MBR would be wiped out making the disc unbootable. Even if you copy the Ubuntu partition it remains unbootable since the stage 1 of Grub is wiped out.

When you reinstall Grub it automatically checks the disc for Ubuntu installation and rewrites stage 2.

Please look for Grub reinstallation elsewhere on this forum.

kagashe

---

### Post by timo1023 on 2007-07-07
Alright, I've found several posts on Grub reinstallation, however I just want to make sure that the whole process of copying partitions will work. Will it, if I reinstall Grub afterwards?

---

### Post by coffeecat on 2007-07-07
**timo1023**, what you are wanting to do is actually easy enough and quite feasible if you have the knowledge and experience, but if you're new to Linux you're going to find it quite daunting. There are  three things you must remember to do.

1 Re-install Grub stage 1 to the mbr (that's the first few hundred bytes) of the hard disk. In fact when you do this you also reinstall stage 1.5 to an otherwise small unused portion immediately after the mbr. Stage 1 invokes Stage 1.5 which in turn invokes stage 2 which is in your /boot/grub directory, at present on hda6. If you reformat your drive you must re-install grub stages 1 and 1.5, because 1.5 will be pointing to the wrong place. Stage 2 will just get copied over with the rest of your installation.

2 Then you must do something about /boot/grub/menu.lst - this is the grub configuration file - which at the moment will be telling the system that the kernel and initrd.img are in /boot in hda6. Re-installing grub will **not** edit menu.lst for you. You have to do this yourself.

3 Next up you have to do something about /etc/fstab which will have wrong entries for the root partition and swap partition if you reformat. Have a look at [this link.]("http://doc.gwos.org/index.php/Understanding_fstab") An added complication in Ubuntu is that it uses UUIDs to name partitions. To find the UUIDs of your reformatted hard drive you'll have to boot up a live CD first. You'll probably need to do that anyway to do 1 & 2 and edit fstab. But you don't have to use UUIDs - [have a look at this.]("http://wiki.archlinux.org/index.php/Persistent_block_device_naming")

Oh - and do you know you need to prepare a swap partition when you reformat your HD?

I hope I haven't put you off completely - I warned you it would be daunting.

**Edit:** That first link is very good, but you need something a little more straightforward. In fact it links to [this](http://www.tuxfiles.org/linuxhelp/fstab.html) near the bottom of the page.

---

### Post by kagashe on 2007-07-07
> **timo1023 said:**
> Alright, I've found several posts on Grub reinstallation, however I just want to make sure that the whole process of copying partitions will work. Will it, if I reinstall Grub afterwards?
Please read the previous post by coffeecat carefully. What I mentioned previously about Grub reinstallation that it rewrites Stage 2 is not correct. The Grub reinstallation just scans the disc and points to menu.lst it can find. Since the Ubuntu partition is going to change to hda1 from hda6 you need to modify /boot/grub/menu.lst and /etc/fstab manually and create a swap partition as well.

kagashe

---

### Post by Songwind on 2007-07-07
Installing Ubuntu and programs in it isn't that hard or time consuming.  I would think seriously about just backing up your home directories (where the settings are) and reinstalling.  [APTonCD]("http://aptoncd.sourceforge.net/") can make it even easier by backing up the list of all the packages you have installed.

---

