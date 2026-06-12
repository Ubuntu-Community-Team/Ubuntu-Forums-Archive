---
title: "Installing WindowsXP"
date: 2008-04-22
forum: General Help
---

### Post by husseinshatri on 2008-04-22
Hi

I have ubuntu only installed in my Laptop. Actually I have tried to install windowsXP as dual mode. but windows installer can't see my harddisk (I think because of GRUB):(.

I have used Gparted from Ubuntu Live CD and delete all ubuntu partitions and leave my hard disk with only 32FAT partition that should be recognized by windows but it is same. Because I think GRUB still there:confused:.

Could anyone help me on how can I install windows as dual mode. Do I have to remove GRUB first. or reinstall ubuntu then windows.

thank you 
Hussein

---

### Post by silvagroup on 2008-04-22
You'll actually want to install windows first the ubuntu.
Haven't done it in a while but I think if you start with your windows cd in it will start and format your drive, that's why you install windows first.
If Ubuntu is running why not just install virtual box or vmware server and run windows out of there and you won't need to dual boot. Now not all windows apps run on emulator, such as games.So you may need dual boot.

---

### Post by CorvisRex on 2008-04-22
Well, as for Grub, that should not keep the winxp installer from seeing the partitions.  Windows will just install it's own bootloader when it installs.  

Can you be more specific as to the problem. How is your drive partitioned.  I'm assuming only one drive?  What happens durring the xp install process, and when?

---

### Post by ymx on 2008-04-23
Is your laptop using SATA hard drives? Windows XP does not contain drivers for sata hard drive by default. You can integrate the driver to install disk by software such as nlite, or turn off achi mode in BIOS.

Regards.

---

