---
title: "I have a grub related problem..."
date: 2008-05-25
forum: General Help
---

### Post by diablo75 on 2008-05-25
A while back, I wrote a very long guide for installing Windows XP AFTER ubuntu by using a gparted live CD to shrink the primary ext3 partition, install XP in a new partition in the unallocated space, then reboot and use the grub on the Ubuntu Live CD to modify grub so Ubuntu will boot as well as present the user with a menu item for Windows as well.  The guide can be found here:

[http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted](http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted)

Someone attempted to follow the guide and they are having some trouble.  I'm not exactly sure what to tell them, but here's what they said in a comment:

> It didn’t work for me.

I have a separate drive for XP. It’s a second SATA chained to the master, which is Ubuntu. It boots into Ubuntu fine, and I amended the file once to point to the actual disk with XP on sda1 = (hd0,0)

This didn’t work.

So I looked at the file in more detail and found that Ubuntu is listed as (hd0,0) - so i tried changing the ref to the XP disk to (hd1,0).

This didn’t work either.

Then I thought, well I will change the Ubuntu disk references to (hd1,0) as it’s actually on sdb1,2 and 5.

This gave me a menu of options to choose from (which is what I’m after), unfortunately none of the selections worked.

So I booted from the Live CD and changed the boot back to saying hd0,0 for ubuntu and hd1,0 for xp. I still cant boot into xp (even changing the bios to select that disk doesnt work), but at least ubuntu is working again.

Oh what fun. I have to say after 3 weeks trying to get this … system working properly and reinstate my xp data (stuck in an image file on an external disk - well its on my ubuntu desktop as well), i am beginning to get very bored with the whole thing.

Anyone know what he might have done?

---

### Post by VMC on 2008-05-25
Can you have him output the 'fdisk -l' , with everything plugged in, so we can see for ourselves what's what?

Also output 'fstab', there could be a clue there as well.

---

### Post by meierfra. on 2008-05-25
Try

title Windows
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1


If this does not work,  follow VMC advice and post the output of "sudo fdisk -l"

---

### Post by Nameless Neko on 2008-05-25
> **meierfra. said:**
> Try

title Windows
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1


If this does not work,  follow VMC advice and post the output of "sudo fdisk -l"Exactly what I have to do to get mine working.  Have him try this before anything else.

---

