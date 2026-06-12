---
title: "About dual booting."
date: 2016-01-05
forum: General Help
---

### Post by RJ_Donald on 2016-01-05
Is it possible to configure dual booting so it opens only Windows 7 and vice versa unless I press a key?

---

### Post by yancek on 2016-01-05
If you want to boot windows 7 by default, you change the line in the /etc/default/grub file below to the correct menuentry number.  To boot another option, use the down arrow key to highlight it and hit the enter key.

> 
GRUB_DEFAULT=0

---

### Post by RJ_Donald on 2016-01-05
Yes, but still, what I mean is I don't want the menu for dual booting to open up unless I press a key.

---

### Post by yancek on 2016-01-05
You could try the suggestions at the link below.

[http://askubuntu.com/questions/117525/hide-grub2-menu-unless-you-hold-down-shift-key-how-to-make-this-happen](http://askubuntu.com/questions/117525/hide-grub2-menu-unless-you-hold-down-shift-key-how-to-make-this-happen)

---

### Post by pfeiffep on 2016-01-05
I have configured my desktop PC in such a manner that I use the boot menu provided by pressing the esc key on my HP and select either the Windows or Ubuntu boot drive. 
This of course requires that 2 physical drives are present.

---

### Post by Cavsfan on 2016-01-05
> **RJ_Donald said:**
> Is it possible to configure dual booting so it opens only Windows 7 and vice versa unless I press a key?

Personally, I know of no way to do that.
I'm currently Tri-booting Windows 10, Arch Linux and Xubuntu Xenial Xerus 16.04 and have a nice grub screen to look at also. But I've had as many as 8-10 systems on this one drive.
I have it set to default to Windows 10 mainly for my wife.

I had some help from some knowledgeable people creating the wiki and it works flawlessly every time. 
It never needs changing unless you remove or install a new OS.

You'll find directions how to achieve this in the first post of the green link in my signature.

My current grub screen:  [[IMG]http://en.zimagez.com/miniature/20160105174014.jpg[/IMG]]("http://en.zimagez.com/zimage/20160105174014.php")

In Ubuntu there are 3 colors: one for top and bottom and one for the box and normal menu entries and then one for highlighted menu entry.
This grub is on Arch and only the box and the menu colors were changeable - I have it set to cyan and red which works well with that picture.

Cheers

---

