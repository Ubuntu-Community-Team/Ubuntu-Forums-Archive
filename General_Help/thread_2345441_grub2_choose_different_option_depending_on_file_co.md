---
title: "grub2 choose different option depending on file content"
date: 2016-12-04
forum: General Help
---

### Post by garlorsus on 2016-12-04
I want to boot a computer with a different OS depending on different  things, the ideal setup would be for grub to read a file in the network  and act accordingly, but afaik this is impossible

so what about  read a file either on ntfs or ext4 partition and act depending on this,  is it possible?, have been looking about how to do this but have found  nothing

---

### Post by Cavsfan on 2016-12-04
> **garlorsus said:**
> I want to boot a computer with a different OS depending on different  things, the ideal setup would be for grub to read a file in the network  and act accordingly, but afaik this is impossible

so what about  read a file either on ntfs or ext4 partition and act depending on this,  is it possible?, have been looking about how to do this but have found  nothing

AFAIK, there is no way for grub to read a file to get the bootable partitions.

Here is a link to explain what Grub 2 can do. [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

The output of **sudo update-grub** goes in **/boot/grub/grub.cfg**.

Then there is the green link in my signature if you want a custom grub, which you setup and once done, nothing ever changes unless you remove or add an OS.
You can setup the default line you want to boot into.

---

### Post by oldfred on 2016-12-04
What things?

My old OS/2 used to have a button to choose which system to reboot into Windows or OS/2. Not sure what it did, but with my current understanding it may have been a dd to MBR or change of boot flag.

But I have install grub to NTFS, FAT32 & Linux partitions. So it would be possible to install grub to a NTFS partition. And then have 3 grub files (or more). One is your actual grub.cfg. But then you have a Windows default and a Linux default and run a script to copy which every system you want as grub.cfg.
Since not installed inside Ubuntu, you would have to totally maintain your grub.cfg. It would not be running os-prober nor reading configuration settings from /etc/default/grub. You would have to add what you need manually.

---

