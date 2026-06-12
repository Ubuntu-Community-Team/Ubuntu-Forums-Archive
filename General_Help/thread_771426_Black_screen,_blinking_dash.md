---
title: "Black screen, blinking dash"
date: 2008-04-27
forum: General Help
---

### Post by Boris and Bailey on 2008-04-27
I have installed a Nvidia GeForce 8400 video card and now I cannot get into Ubuntu. First, the Nvidia text appears, then the ASUS logo appears, then there is nothing but a black screen a a blinking dash in the upper left corner. No key combinations will work. I erased the hard disk and installed Hardy Heron. Would anyone know what I can do to get into Ubuntu?

---

### Post by ibuclaw on 2008-04-27
Do you get past the GRUB boot stage?

Have you tried switching through the virtual terminals?

They start from **Ctrl+Alt+F1** through to **Ctrl+Alt+F7**

Regards
Iain

---

### Post by Boris and Bailey on 2008-04-27
thank you for your response. Actually, I don't even get into the GRUB boot stage. After the initial Nvidia text and the ASUS motherboard logo screens, it goes directly into a black screen with a blinking dash.

I'd love to have the GRUB boot stage show up. I have Ubuntu on one drive, Windows on a second drive. GRUB would show up with the two choices. Not any more! Just the black screen and a blinking dash. Ctl-alt-F1 through F7 don't work. Anyone know how I can get GRUB to show up so I can get into Ubuntu?

---

### Post by ibuclaw on 2008-04-27
I think, if what you say is precisely accurate. That the problem is that the master boot record may be gone!

[QUOTE=Boris and Bailey]it goes directly into a black screen with a blinking dash.[/QUOTE]
Sounds like the motherboard may just be sitting there dormant, waiting for an instruction that it'll never get.

Reinsert your Ubuntu LiveCD and reboot the computer into the Live Environment.

Mount your Linux partition (open it in Nautilus) and go into **boot/grub/** and check that the file **menu.lst** is there.

Regards
Iain

---

### Post by Boris and Bailey on 2008-04-27
Menu.lst appears in the Grub folder.

So menu.lst is there but GRUB will not load. When I fire it up, the copy describing the Nvidia graphics card comes up first, the ASUS logo comes second. Third, the GRUB menu should come up but it doesn't. Instead, there is a black screen and a blinking dash.

The Nvidia 8400 Gforce graphics card was the last thing I installed before problems arose. The problems persist even if I remove the card and plug the monitor into the port that goes to the former embedded graphics.

Bottom line: New video card installed; hard disk erased; Hardy Heron installed; menu.lst is there; GRUB will not load.

Any answers?

---

### Post by ibuclaw on 2008-04-27
Okay, lets see if this worth a shot.

[EDIT]
NOTE: All text labelled in **bold** are to be replaced with values specific to your system.

1) If your not already in it. Load up the Ubuntu LiveCD. And mount your linux filesystem.
Then chroot to it:
```
sudo chroot /media/**sda1**
```

2) I'd recommend that you back-up any files that you'd rather save.

3) Open a terminal and type in:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

4) Now we'll open grub
```
sudo grub
```
You'll be brought into the grub command prompt.

5) Type in
```
find /boot/grub/stage1
```
If it can't find it, mount all hard-drives and try it again.
you'll get an answer like:
> (hd1,9)

6) Now, take that answer and put it in this command:
```
root **(hd1,9)**
```

7) And finally:
```
setup **(hd1)**
```

Then type:
```

quit
reboot

```

We'll see if there is an improvement with GRUBs default settings first.
And may look into altering the menu.lst file later.

Regards
Iain

---

### Post by ryanhaigh on 2008-04-27
I would recommend checking your bios to see what device is set to boot from, if it is detecting the hard drives, maybe reset all to defaults and then change to boot from hard drive first again.

---

### Post by Boris and Bailey on 2008-04-28
Thank you for your replies!

Now we're getting somewhere. I did find a thread some time ago about getting into GRUB and the instructions were close to yours, minus the first three points. I think I'll try yours out (even if it's redundant--can't hurt anything) to see what I come up with.

So far, I come up with errors 17 and 13. Menu.lst has the Ubuntu kernel on hd1/0; however, it also shows Windows as hd0,0 and Ubuntu as hd0,1. Doesn't make sense to me...yet. The MBR now has it set at hd1.

As for the BIOS, I always have it to start up with the CD/ROM drive first, then the two SATA hard disks. If there is no CD in the CD/ROM drive, it goes directly to the disks. The BIOS doesn't seem to have a numerical order for the disks.

I think I'm getting closer to resolving this.

Many thanks to you two. If you have any ideas on how I should change menu.lst, that would be welcomed!

---

### Post by ryanhaigh on 2008-04-28
Boot from the livecd, find the uuid of your root partition, and use root=UUID=theuuidyoufound in the menu.lst of your installed system. 

Although tinivoles instructions should work without having to do this.

---

### Post by ibuclaw on 2008-04-28
Have you had any luck on the matter yet?

Error 17 usually means that you are pointing GRUB to the wrong filesystem.

Error 13... Well, is a little more vague, but usually denotes a corrupt filesystem. Which as far as I'm aware is false. You can mount all your filesystems in Ubuntu, can you not?

> Menu.lst has the Ubuntu kernel on hd1/0; however, it also shows Windows as hd0,0 and Ubuntu as hd0,1. Doesn't make sense to me...yet. The MBR now has it set at hd1.

Did you make a backup copy of the menu.lst file?, as I asked.
It was one of the first instructions in my list.

[QUOTE=tinivole]
Code:
**sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak**
[/QUOTE]
If all went well, go into your linux filesystem with Nautilus (a nice graphical view). Enter /boot/grub and check that the "**menu.lst.bak**" file is there.

If it is, rename the current "**menu.lst**" to, say "**menu.lst.old**" and rename that backed up one back to "**menu.lst**" again.

Regards
Iain

---

### Post by jpp128 on 2009-04-30
1

---

