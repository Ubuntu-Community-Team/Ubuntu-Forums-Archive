---
title: "General Uninstallation Question"
date: 2008-02-09
forum: General Help
---

### Post by blobinator11 on 2008-02-09
First, thanks for reading this. Second, I'm sorry if this is the wrong help thread, I looked at all the others and this section looked the most appropriate for my question. And yes, I've searched... multiple times.

My question is how to completely erase the Ubuntu (ext2) partition. I know how to uninstall the GRUB bootloader through my Windows installation disk, but Ubuntu is taking up space I may need in the future. I don't need the space now, but my hard-drive is filling up and it'd be useful if I knew how to uninstall in case I had too. I love Ubuntu, but I might have to temporarily un-install it until I get more space, or I could use my Live CD :lolflag:

Anyway, my question is how to completely format and delete Ubuntu without harming the files I already have on my C:\ drive. I currently have Windows XP installed.

I've heard I can format the ext2 partition on my C:\ drive using my Ubuntu Live CD, but I don't know how. I'm also not sure if it would leave my Windows installation (and all the files) alone also.

**Thanks for your time!** :)

---

### Post by Rocket2DMn on 2008-02-09
You can either erase the Ubuntu partitions (/ and swap) from the LiveCD using GParted (System->Administration->Partition Editor) or the [GParted LiveCD]("http://gparted-livecd.tuxfamily.org/"), or you can boot into windows and format from there.  To get rid of grub, boot from your windows disc and enter the recovery console and run
```
fixmbr
```
You will then have only windows.
If you want to add the space back to your windows partition, you will need to use one of the first 2 options to delete the Ubuntu partition(s) and "grow" the windows partition.  If you do this, please make sure all of your important stuff is backed up, fiddling with partitions can be dangerous.

---

