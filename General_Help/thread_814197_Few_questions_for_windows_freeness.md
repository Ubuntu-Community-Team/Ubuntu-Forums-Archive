---
title: "Few questions for windows freeness"
date: 2008-05-31
forum: General Help
---

### Post by jbaerbock on 2008-05-31
Ok so since I finally got WoW working in wine I want to get rid of Windows and this dual boot beast. This is the way I planned on doing it since I don't want to re-install (got everything set-up nice).

1. Zap windows partition and add it to current ubuntu home partition using gparted.

2. Change grub so it loads newest ubuntu by default with barely any delay. (need help on this part).

Lemme know if any of this won't work and any instructions on how to edit grub for the things mentioned would be appreciated. Thanks again everyone.

---

### Post by vvvladut on 2008-05-31
There is a nice package called QGRUBEditor that lets you edit your GRUB menu and do all sorts of things to it - very useful. It's QT but it works in Gnome as well. It even lets you set the menu delay to 0.

I think there is another one that's GTK (Gnome native), just search for GRUB menu editor in Synaptic.

Does this answer your second question?

---

### Post by Rocket2DMn on 2008-05-31
That looks right.  You will need to use the Ubuntu LiveCD or [GParted LiveCD]("http://gparted-livecd.tuxfamily.org/") to resize your root partition since it can't be modified while it's mounted.  Of course, you should always have complete and up to date backups of everything that is important because fiddling with partitions can be dangerous (you're actually more likely to screw it up than the partitioner is).

GRUB will be updated using the menu.lst file
```
gksudo gedit /boot/grub/menu.lst
```
You can remove the windows entry from there and set the "timeout" property to something lower than 10, like 5 or 3 seconds.

---

### Post by jbaerbock on 2008-05-31
Ok then that should answer it all. I always figure messing with partitions could end up being evil for me but thus far have yet to have problems with the resizing windows partitions thing. Oh and KGrubEditor is the QT one QGrubEditor is GTK I do beleive.

---

### Post by Nathan_M on 2008-05-31
If you want to edit grub manually (when I started with Linux, that's how I did it, and it's only recently I've discovered GRUB GUIs), here's how:

$ sudo gedit /boot/grub/menu.lst

add these lines (or adjust as appropriate if something similar is already there):

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

I don't think it matters where you add them... on mine it's near the top, just below the timeout bit. These lines set it so you don't see the menu at all, unless you press Esc. Alternatively, you can set the menu timeout to 2 or 3 seconds... it's up to you.

Now all you need to do is remove the Windows part:

title		Microsoft Windows Vista
root		(hd0,1)
makeactive
chainloader	+1

If the lines you remove are at the end of the file, make sure the file ends with a new line. And that's it. Save and close.

P.S. I recommend doing it manually... that's how you'll learn your way around.

---

### Post by jbaerbock on 2008-05-31
Ok thanks a lot, that'll help. I'm just so freakin glad I'll be rid of windows :D

---

### Post by jbaerbock on 2008-06-01
Ok so I tried to add the unallocated space to the main ext3 partition, however I saw no way to do this in gparted. Is there something I missed? Having it as a seperate partition is kind of odd.

---

### Post by Rocket2DMn on 2008-06-01
Have you used the GParted LiveCD like I suggested?  If the two partitions are next to eachother, you should be able to delete the ntfs partition and expand/grow the Ubuntu partition into that empty space.

---

### Post by jbaerbock on 2008-06-01
Yeah was using the LiveCD, ain't that much of a newbie lol.
And then clicked on resize ext3 partition (the unallocated space was above the hda2 (under which were the partitions linux is on) but it didnt let me expand it all I could do (but didnt) was make it smaller.

---

### Post by meierfra. on 2008-06-01
> And then clicked on resize ext3 partition (the unallocated space was above the hda2 (under which were the partitions linux is on) but it didnt let me expand it all I could do (but didnt) was make it smaller

You first have  to expand the extended partition, which contains the  ubuntu partition.

---

### Post by lisati on 2008-06-01
> **Rocket2DMn said:**
>  you should always have complete and up to date backups of everything that is important because fiddling with partitions can be dangerous (you're actually more likely to screw it up than the partitioner is).


+1: been there, done that! 

Good luck to the OP, and take care.

---

### Post by Rocket2DMn on 2008-06-01
> **jbaerbock said:**
> Yeah was using the LiveCD, ain't that much of a newbie lol.
And then clicked on resize ext3 partition (the unallocated space was above the hda2 (under which were the partitions linux is on) but it didnt let me expand it all I could do (but didnt) was make it smaller.

> **meierfra. said:**
> You first have  to expand the extended partition, which contains the  ubuntu partition.

If the OP is using extended partitions, then this is true.  You can post a screenshot for us if you don't figure it out, or post
```
sudo fdisk -l
```
If you are on the Ubuntu LiveCD, I believe it mounts your swap partition, so you may need to unmount that before it will let you resize (like if it is also in the extended partition).  The GParted LiveCD doesn't automount the swap partition, so that shouldn't be a problem with the GParted LiveCD.

---

### Post by housam on 2008-06-01
Boot from the live cd and go for system >> admin. >> partition editor and take a screen shot of the image and post it please.( for the screen shot : go for applications >> accessories >> take a screenshot ) this will help explain the point.

---

### Post by jbaerbock on 2008-06-01
Yeah I got it figured out. Had to copy the hda2 into the unallocated space which made the unalocated fall under hda2 then just expanded ext3 and am golden :D.

---

