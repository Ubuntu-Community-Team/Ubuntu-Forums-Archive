---
title: "Creating an Ubuntu system image in dual boot"
date: 2014-12-19
forum: General Help
---

### Post by Gordonbp531 on 2014-12-19
I have a dual boot setup - Ubuntu 14.04 and Windows 8.1
What I'm wanting to do is to create a System image of the Ubuntu install only, such that if I need to I can restore from that image, but that also it re-instates GRUB at the same time, which is installed on the EFI partition.
Is this feasible, and what would be the best way to do this?

Thanks

---

### Post by sudodus on 2014-12-19
The simplest way would be to make a compressed image of the whole drive with Clonezilla. That would include Windows too.

If you don't want to backup Windows (this way), you can make an image of all the partitions involved in Ubuntu (including the EFI partition) also using Clonezilla. It will show you what a command line looks like, to use directly for new and updated images (instead of re-configuring with the menu interface), so if you save that command line, you have a quick option.

Images of the partitions will not include the boot sector, you must reinstall that separately, if you want to restore the system into a new drive.

There are several other tools that can to similar things, some of them are based on rsync (a command line tool).

-o-

You can only rely on a backup system, that you have tested, and to test it you need not only one drive to store the compressed image, but also a drive of at least the same size as the original one, where you can restore the system and check that it really works.

---

