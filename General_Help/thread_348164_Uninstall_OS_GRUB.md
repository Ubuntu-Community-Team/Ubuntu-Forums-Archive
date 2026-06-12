---
title: "Uninstall OS GRUB"
date: 2007-01-28
forum: General Help
---

### Post by evildrummer on 2007-01-28
I have been experimenting with linux more and more recently and I decided to move my linux from an old spare box to my main machine, but I needed to keep windows on, so I dual-booted with GRUB, but there were some problems so now, I have a partition with a working linux, a partition with a broken linux and a windows partition (I think two actuallY) what I need to know is how can I remove both linux's so I can start again with 6.10, I need to keep windows and it would be good if I can restore the space to windows.

Much thanks in advance,
Stuart

---

### Post by meng on 2007-01-28
You can use a 6.10 install disk (either Desktop or Alternate) to delete the existing Linux partitions, resize the Windows partition and then install a fresh Ubuntu system (and grub) on what's left.

Or, if you encounter problems with this, download and use the GParted Live CD to do the partitioning work before you do the install.

---

### Post by Tomosaur on 2007-01-28
As meng said - you can delete the two linux partitions using the partitioner on the Ubuntu LiveCD. You can then reformat the newly created space as a different filesystem.

After that, you will need to restore the MBR back to Windows (so that grub doesn't boot) - but for this you need a WinXP recovery CD, or some other bootloader of your choice.

---

### Post by evildrummer on 2007-01-28
I would still like GRUB as I am going to still have a ubuntu partition is what 'meg' said possible and just delete the partitions AND install a freash one at the same time possible? I dont know where my win XP disk is.

Also how can I tell which partition is which?

---

### Post by evildrummer on 2007-01-28
I think I know what I am going to do but I need to know if it is possible:

I am going to boot into live CD, and get rid of both linux partitions
LEAVE GRUB on there, I think it should still be able to boot into windows
then de-fragment my disk so all space is for windows and my computer is normal again
then re-install linux, would it work?

---

### Post by Tomosaur on 2007-01-28
No, it wouldn't. Grub needs a Linux installation present to work properly. You can delete the two Linux partitions, and then reinstall Linux on the freed up space. This will also reinstall grub so that it'll all work smoothly. If you just delete the two linux partitions, grub will remain on the MBR, but will give you an error when you boot up, and you will be unable to boot into windows or linux. You either have to reinstall Linux, or get rid of Grub altogether by overwriting it using the Windows XP disk. Since you don't have your XP disk, your only choice is to reinstall Ubuntu on the freed up space - or search for an alternative bootloader.

---

### Post by evildrummer on 2007-01-28
ok, thank you, I will do that now. THank you ever so much and ill tell you how it all goes

---

