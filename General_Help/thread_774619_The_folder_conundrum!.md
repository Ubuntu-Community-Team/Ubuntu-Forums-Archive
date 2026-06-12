---
title: "The folder conundrum!"
date: 2008-04-29
forum: General Help
---

### Post by JewelledDragon13 on 2008-04-29
Unadvisedly trying to make my Hardy like my old Feisty, I pulled a link to my home folder onto my desktop.  Anyway, that was the plan.  Unfortunately, Hardy seems to interpret this by actually putting a copy of my home folder on my desktop.  The home folder itself of course contains my desktop, which now contains my home folder, which contains my desktop, etc etc ad infinitum.

As this wasn't exactly what I wanted, I deleted the folder off my desktop.  Only now it is in my trash, still containing my desktop, and my home folder, and my desktop, and so on, so that it thinks it has an infinite number of files.  I can't permanently delete it because it can't do the file operation with an infinite number of files.

Aside from point and laugh at myself, what should I do?

---

### Post by victor.zamanian on 2008-04-29
This seems like an april fool's joke to me. You're not kidding us are you? :)

As far as I know, links to folders can only be soft (not hard links) and shouldn't cause any problems like that... if nautilus is telling you it can't delete the link, copy it back to the Desktop (from the Trash) and open up gnome-terminal and just rm it. That ought to do the trick, unless I'm not understanding the problem correctly.

So, again:
-------------------------------------
* Copy link back to Desktop
* Press Alt+F2, type "gnome-terminal"
* $ rm ~/Desktop/<file name of link>
-------------------------------------

I hope it works out. And please, take no offense to my initial reaction. :O

---

### Post by drewcoon on 2008-04-29
LOL! I thought you were kidding too, but then I started divining infinity on my own computer,

[img]http://i16.photobucket.com/albums/b23/Drewc2k5/Screenshot-nautilus.png[/img]

:o looks like bugginess like this *does* exist.

---

### Post by JewelledDragon13 on 2008-04-30
Alas, I can't copy it back to my desktop because it thinks it's an infinite number of files.  Here's a screenshot.

[IMG]http://farm4.static.flickr.com/3098/2455688528_95d775371c.jpg?v=0[/IMG]

Should I file a bug report?

---

