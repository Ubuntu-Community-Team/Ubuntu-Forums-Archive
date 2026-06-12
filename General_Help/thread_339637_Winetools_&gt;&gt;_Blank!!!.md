---
title: "Winetools &gt;&gt; Blank?!?!!?"
date: 2007-01-16
forum: General Help
---

### Post by icehammer on 2007-01-16
I installed wine and wine tools, reading help from a post in this forum only..

[http://ubuntuforums.org/showthread.php?t=149585]("http://ubuntuforums.org/showthread.php?t=149585")

But the site given for winetools wasn't responding, so i got the package (same version from another site, same filename).. Now, when i open winetools.. No text is visible!!!

SEE attachment(s). How am i supposed to know what to do?? In the last screenshot, the text doesn't work either.. if it is a  textbox, i dunno.

Please advise..

---

### Post by frodon on 2007-01-16
I give you the link to a really detailed guide about wine :
[http://doc.gwos.org/index.php/HowToWine](http://doc.gwos.org/index.php/HowToWine)

You should remove your winetool package and follow this guide, there're other ways than winetool to configure wine, i used winecfg in my case.

---

### Post by Pasa Yildirim on 2007-03-27
Hello!

The problem is because of fonts in GTK 1.2.

Type

```
sudo gedit /etc/gtk/gtkrc.utf8
``` (or gtkrc.yourlocale) and change this:

```
class "GtkWidget" style "default-font"
``` (or similar)
to
```
class "GtkWidget" style "user-font"
```.

Then it will work. Good luck!

---

