---
title: "How to remove Lucid from triple boot (Win and PP) and keep it's directories intact?"
date: 2013-03-31
forum: General Help
---

### Post by emarkay on 2013-03-31
Since Lucid is running out of life, I have a triple boot with Precise and WinXP and want to remove the program and its boot entries, but keep all the data files.  Is this possible without having to copy and reload; can I just "kill" Lucid and leave everything intact?  Just want a dual boot and the remaining data directories from Lucid where they were.  

Thanks!

---

### Post by grahammechanical on 2013-03-31
When we run the command ```
sudo update-grub
``` then a utility will search the hard disk for operating systems. At the moment that Grub utility is finding Lucid, Precise, and XP on your hard disk and creating a boot menu with those options. If you
 
1) boot into Lucid and move/remove/delete all the Linux images in /boot/ then that will effectively kill Lucid. But none of the others files and folders will be removed/deleted.

2) Boot into Precise and run ```
sudo update-grub
``` and ```
sudo grub-install /dev/sda
``` then the Grub utility will look for operating systems but will not find Lucid. It will create a boot menu with only Precise and XP on it. The second command installs Grub into the MBR of the first hard disk. That second command is sometimes necessary.

Regards.

---

### Post by emarkay on 2013-03-31
> move/remove/delete all the Linux images in /boot/
There are  multiple linux-looking files  there: abi..., config..., initrd..., system.map..., vimlin... - delete all or some of htese?

---

### Post by Impavidus on 2013-04-01
I think the easiest way would be renaming the entire /boot directory (to /boot.backup or something like that). It should kill the system, but at the same time it's reversible, so if the need arises you can still boot your lucid install.

You can also delete all of it, as you won't have any need for those boot files after you killed the OS, but that will not be reversible.

---

### Post by emarkay on 2013-04-10
Thanks! worked great.

---

