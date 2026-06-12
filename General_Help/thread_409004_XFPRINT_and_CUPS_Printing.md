---
title: "XFPRINT and CUPS Printing"
date: 2007-04-14
forum: General Help
---

### Post by phossal on 2007-04-14
Does anyone know how to configure cups and xfprint(4) to play together? Mousepad won't print, because xfprint and cups don't automatically work - even when using the packages. I've heard there is a way. Does anyone know it?

---

### Post by gottferdamnt on 2007-04-21
Up ! please help !

---

### Post by guysmiley25 on 2007-04-21
Im working on the same thing at the moment and I think Ive just fixed it.

Try installing a2ps

sudo aptitude install a2ps

for me it did not work straight away. then I realized that I had not set a default printer so I did in cups and now it works.

I not sure if it was because of the default thing, or because it took time for a2ps to work. Let me know how you get on.

---

### Post by phossal on 2007-04-22
I had already installed it. Mousepad won't even *attempt* to print without xfprint and a2ps. The problem is, it's not connecting to cups. I've read there is a way to connect to the "backend" of cups, but I can't figure it out.

---

### Post by guysmiley25 on 2007-05-05
And cups is configured and working correctly?

Also do you have a default printer set?

---

### Post by phossal on 2007-05-06
I have no idea how to *tell* if cups is configured and working correctly beyond the fact that stuff does print - just not from mousepad. Yes, I have a default printer.

---

### Post by guysmiley25 on 2007-05-06
Very Strage indeed.

What version of ubuntu are you using? xubuntu 6.10?

One thing you could try is loging out and then from gdm, select change sesson, select xfce4 then log back in.

---

### Post by ductipus on 2008-05-19
I run gentoo but had the same problem. In order to have xfprint work with cups I had to run the Xfce settings manager xfce-setting-show, then select Printing system and then choose CUPS from the Printing system selection dialog. After that xfprint4-manager showed the cups printers and I was able to print from mousepad.

Hope this helps.

---

