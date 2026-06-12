---
title: "Need Grub Help: Re-installed and now it won't load windows"
date: 2007-03-14
forum: General Help
---

### Post by tmoneygetpaid on 2007-03-14
Hey, so I had a dual boot system running Ubuntu and XP Home. I recently installed XP Pro and lost GRUB, so I loaded the live cd, and did the following at terminal:

sudo grub
root (hd0,2)
setup (hd0)
quit

this loaded Grub perfectly. I could get back into Ubuntu and get all those files I didn't have access to for a while. But, Grub lists XP Home and when I try to boot that, I get a generic error, "Can't Find Operating System." I tried running fixmbr at windows recovery console, just to overwrite grub because this computer needs to be running XP 24/7 now, and got the same error.

So I need help.

I know there's that menu.lst file I have to mess with, but I'd like some specific help with that. Like, if my Windows installer is on  a unix-named partition hda1 or hda3, what does this correspond to in the menu.lst file and how do I write a correct entry?

Thanks!

---

### Post by arvindkst on 2007-03-14
Try this in the menu.lst

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by silhouette on 2007-03-14
I think hd(0,0) refers to the first drive, first partition. Similarly hd(0,2) refers to the first drive, third partition. See [here](http://www.gnu.org/software/grub/manual/html_node/Naming-convention.html#Naming-convention) for more.

---

