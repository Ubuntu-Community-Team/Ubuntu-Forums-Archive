---
title: "Text beside the Menu/Start button"
date: 2007-03-12
forum: General Help
---

### Post by Exillo on 2007-03-12
Hi,

I like having the minimal all in one menu (rather than apps, places, settings) but I want to have it a bit wider (so it's a similar size to the windows start button). I've seen screenshots of people who have text beside the button to make it wider and was wondering how I can do this.

Thanks in advance! :KS

---

### Post by fragos on 2007-03-12
I'd like that answer as well but haven't come across it yet.  Hopefully someone will know and tell us.

---

### Post by kokiri on 2007-03-12
Right click on your menu/start button, choose remove from panel,
Then right click on the now blank space and choose add to panel
Out of the window that pops up choose Main Menu instead of menu bar

Poof, small mini start/menu button

enjoy

---

### Post by Exillo on 2007-03-13
That's what I already have (sorry if I didn't make that clear) but I want to put text beside it so I have a windows start sized button to click on rather than the small one.

---

### Post by kokiri on 2007-03-13
Ah... sorry bout that... in that case, unfortunately it's either the big Applications Places System button set or its the non texted tiny just icon button.... there isn't an available intermediate as those are hard coded into the gnome panels package, that's not saying one couldn't be created, but one doesn't exist stock as of yet

oh wait, I'm a nut ball.... yeah, you could edit the default main menu icon and add some text to the image and save it, then you'd have the icon and some text with just the tiny icon button

---

### Post by Exillo on 2007-03-13
I'm sure I've seen screenshots of it in the desktop thread that's all... Thanks for the help anyway. =)

---

### Post by kerry_s on 2007-03-13
This is what you can do, go to kde-look and grab one of the kbfx sets you like, than you just need to replace the main menu icon. Of course you don't need a whole set, you only need 1 icon and just dump the rest. That's how i do it in xfce4.

---

### Post by Exillo on 2007-03-13
I'm not entirely sure how to do that sorry... Do I need kde instead of gnome?

---

### Post by kerry_s on 2007-03-13
No, your just changing the small icon to a bigger menu icon. I included the 1 i have as an attachment, so you can try it till you find 1 that makes you happy and fits your theme. :) Icons are just very small pictures, you can change the pics to what ever you want. I like the kbfx icons because there already made for the panel.

first you need to locate the icon->
in terminal run->
sudo updatedb
locate main-menu.png <-adjust name to what it says in the add app for the menu name.

this will give you the locations of the menu.png, now rename the icon i attached to that main menu name and replace the icon(you can rename the original to something like main-menu.png.old or something. Since the icons are on the root side you need to use root nautilus(gksu nautilus / ).

I'm not using gnome, haven't for a long time, so i can't be precise on the exact directions, but i know i did it way back when i used gnome.

Here's a good selection of menu icons you can snag a icon from, click on kbfx in the left menu-> [http://www.kde-look.org/index.php?xcontentmode=62&PHPSESSID=7082826a6fa0b153c63d889b57a8d2db](http://www.kde-look.org/index.php?xcontentmode=62&PHPSESSID=7082826a6fa0b153c63d889b57a8d2db)

---

### Post by Exillo on 2007-03-13
Thanks heaps, I'll try it later on and post how it goes. :D

---

### Post by fragos on 2007-03-13
Thanks here as well.  For my taste, I much prefer the single icon.  For those things I want to get to quickley I use key bindings or drag an icon to the applet bar.

---

### Post by 16777216 on 2007-03-14
If you are using Gnome as your desktop then I believe you are wanting :KS [USP the Ubuntu System Panel]("http://www.ubuntuforums.org/forumdisplay.php?f=156"). :KS Highly customizable and  I believe   that is what you are referring to by the screenshots that have a menu button with text beside it.

---

