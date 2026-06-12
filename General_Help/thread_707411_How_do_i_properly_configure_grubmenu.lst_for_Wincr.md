---
title: "How do i properly configure grub/menu.lst for Wincrap XP"
date: 2008-02-25
forum: General Help
---

### Post by Dojan5 on 2008-02-25
Just a minor HUGE problem now.
I cant boot into Crapodos Windoze XP...
I had to change my /boot/grub/menu.lst
So i did that and added:

title Microcrap Windoze XP
root (hd0,1)
makeactive
chainloader +1

But i think it is this hd0,1 that is the problem. Look to see how my hdd is put up: [http://ubuntuforums.org/attachment.php?attachmentid=60780&d=1203956324](http://ubuntuforums.org/attachment.php?attachmentid=60780&d=1203956324)...
So, how do i configure this entry so it fit my harddrive?

---

### Post by northern lights on 2008-02-25
GRUB's syntax might appear a bit odd a t first, but theoretically you chose right.

(hdx,y) points to the yth partition on the xth harddrive. Where the count starts from 0.

I believe Windows does not particularily like residing anywhere but on the first partition of a drive. In GRUB you can use the "map" command to make Windows believe that that's where it is.

Check [here]("http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows").

Before screwing with your GRUB though, you might wanna wait for someone to confirm. Also, how does the error present itself?

---

### Post by Dojan5 on 2008-02-25
> **northern lights said:**
> GRUB's syntax might appear a bit odd a t first, but theoretically you chose right.

(hdx,y) points to the yth partition on the xth harddrive. Where the count starts from 0.

I believe Windows does not particularily like residing anywhere but on the first partition of a drive. In GRUB you can use the "map" command to make Windows believe that that's where it is.

Check [here]("http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows").

Before screwing with your GRUB though, you might wanna wait for someone to confirm. Also, how does the error present itself?


I dont remember right now..
Ill post here later, after fiddling with GRUB and try...
Thanks
         lll
Error V
"Invalid or Unsupported executable format"

---

### Post by logos34 on 2008-02-25
Yes, you're right--(hd0,1) is windows...theoretically should work. Do not use 'map' commands--those are only needed when windows is on a non-first hard disk.

What's the deal with the huge swap?  You only need ~1 gb.  You can use gparted on the live cd to delete it, make a new smaller one, and expand /home to the left into the remaining space.

---

### Post by northern lights on 2008-02-25
> **logos34 said:**
> Do not use 'map' commands--those are only needed when windows is on a non-first hard disk.

Aight, thought it might have to be on first partition also. That's why I asked to wait for confirmation...

---

### Post by Dojan5 on 2008-02-25
> **logos34 said:**
> Yes, you're right--(hd0,1) is windows...theoretically should work. Do not use 'map' commands--those are only needed when windows is on a non-first hard disk.

What's the deal with the huge swap?  You only need ~1 gb.  You can use gparted on the live cd to delete it, make a new smaller one, and expand /home to the left into the remaining space.

Hahaha i know.
My computer dont even use 1 percent of the swap. :lolflag:
I made it when i installed Ubuntu first time, it was around 3 am and i was REALLY tired, then i created the 15 gb swap.

Okay, now when i use hda0,1 it says:

Disk Error
Press any key to restart

---

### Post by Dojan5 on 2008-02-25
Oh ya, and this is what menu.lst say:

title Windows XP
root (hd0,1)
makeactive
chainloader +1

---

