---
title: "How can I install Windows AFTER I've installed Linux?"
date: 2007-05-18
forum: General Help
---

### Post by freehunt on 2007-05-18
I have Feisty installed, but I would like an install of Windows as well for things Wine can't do. How can I go about managing the bootloader so Windows does not destroy my ability to run Ubuntu?

---

### Post by n8bounds on 2007-05-18
print out /boot/grub/menu.lst

install windows like normal  (assuming you have blank space somewhere on your drive for windows to live, otherwise we'll have to talk about gparted or something to resize what you have to make room)

(unless you have nice hardware, then consider vmware)

once its done, reboot from the ubuntu live cd

open a terminal and reinstall grub

say:

grub

then say (verify this from the menu.lst file you printed, change the numbers if you have to)

root (hd0,0)  

then say

setup (hd0)

then say quit

now reboot

anyway, thats the basic idea, adapt to your setup; if you need help shrinking ubuntu to make room for windows, let me know

---

### Post by freehunt on 2007-05-19
I have a 60gb drive in my laptop, it's not much, but I have 30-40gb free, since I store most of my stuff on my external, so I can partition it fairly well. You intrigue me on "shrinking" Ubuntu, do you have a short synopsis or link you can give out? I don't think I need the full thing explained just right now. I would love to do VMWare, but I am installing Windows for certain games that Wine and Cedega do not support, so I doubt VMware is the best choice. Thanks for the GRUB tutorial, though!

---

### Post by mocqueanh on 2007-05-19
If dont have Live Cd, can i use installion Cd and use Rescue broken system to reinstall GRUB ?

---

### Post by mahy on 2007-05-19
In any case, you have to boot some Linux live cd (e.g. Knoppix) and reinstall grub from it. Like this:

grub-install [wherever]

Replace the [wherever] with the desired location. In my case it's /dev/sda (the MBR of my primary disk).

---

### Post by n8bounds on 2007-05-19
I always use gparted from the sysresccd (a gentoo live cd) 

gparted can resize UNMOUNTED partitions (so, like, Not your root partition you have booted off of from ubuntu), although you can install gparted in ubuntu and do other things with it

its super easy, just fire up gparted from a live cd (knoppix/sysresccd or even ubuntu live cds) and select the partition you want to resize, right click and choose resize then hit apply

---

### Post by Ub1476 on 2007-05-19
Here is a super guide with pictures for every step in dualbooting: [Linky]("http://www.apcstart.com/5459/dualboot_ubuntu_and_windows_xp")

I recommend you to use it, so you wont screw up  your system some way:)

---

