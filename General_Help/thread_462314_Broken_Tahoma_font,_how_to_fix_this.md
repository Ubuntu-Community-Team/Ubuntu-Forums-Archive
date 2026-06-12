---
title: "Broken Tahoma font, how to fix this?"
date: 2007-06-02
forum: General Help
---

### Post by benchMarc on 2007-06-02
I wanted to get the Microsoft fonts into Ubuntu, so that the weird anti-aliasing would be gone. To do this, i followed this tutorial: [http://www.howtoforge.com/sharp_fonts_gnome_p1](http://www.howtoforge.com/sharp_fonts_gnome_p1)

Before that tutorial, i already installed Tahoma myself. The font worked, but was still in anti-aliasing mode. That's why i tried that tutorial. In the middle of the tutorial, my font was suddenly screwed. Now when i select Tahoma it looks like this:

[img]http://www.superstoer.nl/~benchmarc/tahoma.png[/img]

When i select bond or bont italic, the font shows like it should be, but regular or italic is a problem, as you can see in the screenshot. I got regular 2 times there, because i followed a tutorial in a topic here (that really did the trick to get rid of that anti-aliasing this). Now i use Arial, it's quite ok, but i want to get Tahoma working. I already tried to delete all the Tahoma i could find in my Linux partition, but that didn't do the trick.

I'm quite a Linux noob, i use it for 3 days now, but i'm learning fast.

I hope someone can help :) Thanks!

---

### Post by dnzz on 2007-06-02
May be re-installing tahoma font can help. I used this guide and everything works fine.

[http://ubuntuforums.org/archive/index.php/t-82318.html](http://ubuntuforums.org/archive/index.php/t-82318.html)

---

### Post by benchMarc on 2007-06-02
Thanks for the help, but unfortunately it didn't work. It seems i can't get rid of the Tahoma font. Why my system keeps showing the Tahoma font in the Fontlist when i deleted all the Tahoma fonts on my PC? It's just weird.

---

### Post by benchMarc on 2007-06-04
Bump!

---

### Post by benchMarc on 2007-06-04
I found something out. When i open, for example, OpenOffice Word, and i choose the Tahoma font. Then it shows the normale Tahoma font. So it appears the font is only broken in the Linux GUI, and not in other programs.

When i select the font in the Font preferences my whole Linux has those blocks, instead of normal characters. It's a weird problem and i have no idea what's the cause of it.

---

### Post by benchMarc on 2007-06-05
Bump again.

Tried some chmodding, but that didn't do it.

The only path where the font is present is "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".

Maybe there's a link in or another file that links to the wrong Tahoma path? But what file?

---

### Post by subvertigo on 2007-10-20
I have a similar problem.

Previously using 7.04 i had no problem using Tahoma.
Updating to Gutsy, the Regular Tahoma disappeared and only the Bold Tahoma remained.

So I tried to reinstall Tahoma by copying in /usr/share/fonts/truetype the tahoma.ttf and tahomabd.ttf from Windows partitions.

But now Tahoma is definitely broken. When trying using Tahoma i get only the squares, like in the pic above.

I tried everything... "sudo fc-cache -frv", "sudo dpkg-reconfigure fontconfig" and others... no matter...

I noted that when the files tahoma.ttf is outside the /usr/share/fonts directory, Gnome sees its icon correctly, but when in the /usr directory it displays a wrong icon!

Please help I need Tahoma!!!

---

### Post by mkonsel on 2007-10-21
I have the same problem... help

---

### Post by mkonsel on 2007-10-25
up...

---

### Post by flipkick on 2007-11-16
Sorry no solution yet :)

Yeah same here. Upgrade vom Feisty to Gutsy, Regular Tahoma is broken.
Tried cache rebuild, copied several versions as a replacement for the broken version, none seemed to work.


EDIT:

> **yopnono said:**
> Check the permission on them

That worked for me as well.

---

### Post by Bobolin on 2007-11-16
View permissions on te tahoma.ttf, Just need to add read permissions to the file tahoma.ttf because they are missing.
Sorry for my english. :)

---

