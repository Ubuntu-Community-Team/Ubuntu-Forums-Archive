---
title: "Editing menu.lst safely"
date: 2007-06-10
forum: General Help
---

### Post by Geekkit on 2007-06-10
Hi all. Just wondering if anyone has any advice on safely editing my menu.lst. I have some older boot options. I had several partitions on two different disks which amounted to two different installs of Ubuntu and one install of XP. Well, I only need the one operating system (7.04 of course!) and now I would like to get rid of some of those boot options that are not even applicable. I've looked into the menu.lst file but I'm afraid of making a mistake in there and borking my Ubuntu install (it's perfect right now so I don't want to have to redo this :D ).

I came across a post about GrubED but I'm not sure if that one is safe or not or if there's another GUI editor that might work. I also have startupmanager but it doesn't offer choices to edit the menu list (although it does allow one to add background images which is quite funky). Sorry, I'm rambling. Any thoughts/flames?

:)

---

### Post by merlinus on 2007-06-10
In a terminal:

sudo cp /boot/grub/menu.lst /boot/grub/menu_old.lst

Then if you make a mistake, you can copy it back to the original, even from a terminal using a live cd.

To edit the original:

gksudo gedit /boot/grub/menu.lst

-merlin

---

### Post by Shazaam on 2007-06-10
What merlinus said:D

The safest way is to comment out the os listings that you dont need. Put a # in front of them (all except "Recovery Mode").

example only=
timeout 30
color black/cyan yellow/cyan
default 0

title linux
kernel (hd0,0)/boot/vmlinuz root=/dev/hda1  splash=silent vga=788
initrd (hd0,0)/boot/initrd.img

#title linux-nonfb
#kernel (hd0,0)/boot/vmlinuz root=/dev/hda1  splash=silent
#initrd (hd0,0)/boot/initrd.img

title failsafe
kernel (hd0,0)/boot/vmlinuz root=/dev/hda1 failsafe
initrd (hd0,0)/boot/initrd.img

---

### Post by Geekkit on 2007-06-10
Thanks both of you!

---

