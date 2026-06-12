---
title: "How do I figure out which disk is which?"
date: 2007-05-28
forum: General Help
---

### Post by LodeRunner on 2007-05-28
Just upgraded my desktop from Dapper to Feisty and I am sorely missing the gui disk manager (not sure what it was called--was found under (System=>Administration and the launcher was simply called "Disks", I think.) A bit of searching leads me to suspect the (apparently) now-defunct program "disks-admin".  It appears to be installed, but returns nothing but a prompt when entered into a terminal (with or without sudo.)

I read somewhere else that baobab was intended to be the replacement disk management gui, but this appears to show only the file system--not the physical devices.  I really need to be able to differentiate between all of the HDAs/SDAs at a glance...  is there an option that would allow me to do this in baobab? Is there another gui disk manager I could download to replace the old one?  If not, which command line program(s) could I use to figure out which drive is which? (other than trial-and-error mounting, checking, and umounting...)

---

### Post by LodeRunner on 2007-05-28
Well I've noticed that the pissed-off posts tend to get more attention, so here goes:

<noob rant>

People on IRC are telling me to use df or fdisk, neither of which return anything useful (...alone, anyway.)   I understand why stagnate software has been excluded from Ubuntu, but what the **hell** is the rationale behind making it (apparently) impossible to find out any information about unmounted disk drives? Having to mount a disk drive just to find out whether or not it's the one I wish to mount is just about the **stupidest** damn thing I've ever heard, (and in my present situation, completely impossible because the drive isn't directly mountable)... it's completely retarded, it's why Ubuntu is failing to overtake Windows, blahblahflamebait etc.

</noob rant>

I could always be [even less  subtle]("http://bash.org/?152037") about it...

Yeah ok, how about this:

**UBUNTU SUCKS!**  UNLIKE WINDOWS, YOU CAN'T FIND OUT *ANYTHING* ABOUT A DISK DRIVE (OR EVEN LOCATE IT AMIDST A SEA OF HDAs AND SDAs!) WITHOUT MOUNTING IT FIRST!

*waits patiently*

---

### Post by dagrump on 2007-05-29
Try gparted, I'm not sure if it will get you what you need, but it's useful to have. There is also a gparted live disk @ sourceforge that might serve you better and is very handy. Oh really need to work on rants, properly done will make the thread disappear. Your rant just wasn't up to par with some I've seen. Good luck.

---

### Post by LodeRunner on 2007-05-29
> **dagrump said:**
> Try gparted, I'm not sure if it will get you what you need, but it's useful to have. There is also a gparted live disk @ sourceforge that might serve you better and is very handy. Oh really need to work on rants, properly done will make the thread disappear. Your rant just wasn't up to par with some I've seen. Good luck.

Oh hell, I had forgotten about Gparted entirely.  Works like a charm, thanks.

As for the rant, it wasn't and shall never be done properly because I simply like Ubuntu too damn much.

---

