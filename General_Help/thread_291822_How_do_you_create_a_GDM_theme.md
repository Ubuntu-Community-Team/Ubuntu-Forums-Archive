---
title: "How do you create a GDM theme?"
date: 2006-11-03
forum: General Help
---

### Post by randell6564 on 2006-11-03
Hey folks!
Can anyone direct me to a tutorial on creating a working GDM theme?

Thanks!

---

### Post by aysiu on 2006-11-03
> **randell6564 said:**
> Hey folks!
Can anyone direct me to a tutorial on creating a working GDM theme?

Thanks!
How about this one?
[http://live.gnome.org/GnomeArt/Tutorials/GdmThemes#head-c88c5d81cb55ce0da1b121759067d547f1e7748c](http://live.gnome.org/GnomeArt/Tutorials/GdmThemes#head-c88c5d81cb55ce0da1b121759067d547f1e7748c)

---

### Post by randell6564 on 2006-11-03
> **aysiu said:**
> How about this one?
[http://live.gnome.org/GnomeArt/Tutorials/GdmThemes#head-c88c5d81cb55ce0da1b121759067d547f1e7748c](http://live.gnome.org/GnomeArt/Tutorials/GdmThemes#head-c88c5d81cb55ce0da1b121759067d547f1e7748c)

Thanks aysiu!

---

### Post by autocrosser on 2006-11-03
And also a big THANK YOU!!   aysiu!!!

I've been looking for that!!!

---

### Post by randell6564 on 2006-11-03
Hey aysiu!
Sorry but I'm still a bit confused!  [This]("http://live.gnome.org/GnomeArt/Tutorials/GdmThemes#head-1759e04540520a16044d536b2be48657d5998ae5") makes no sense to me! I'm pretty much still a newb when it comes to this kind of stuff!
What the heck does, "The image must be placed in the theme directory and declared in the xml file as follows:" mean?

Again, I apologize, but is there a more step-by-step method? One directed more towards the new guy?
Thanks!

---

### Post by aysiu on 2006-11-03
> **randell6564 said:**
> Hey aysiu!
Sorry but I'm still a bit confused!  [This]("http://live.gnome.org/GnomeArt/Tutorials/GdmThemes#head-1759e04540520a16044d536b2be48657d5998ae5") makes no sense to me! I'm pretty much still a newb when it comes to this kind of stuff!
What the heck does, "The image must be placed in the theme directory and declared in the xml file as follows:" mean?

Again, I apologize, but is there a more step-by-step method? One directed more towards the new guy?
Thanks!
Honestly, I think your best bet is to take an existing GDM theme and then just modify the files within it.

That way, you know it works, and you don't have to start from scratch.

Try this: ```
cd ~/Desktop
wget -c http://www.gnome-look.org/content/files/15994-tuxmania.tar.gz
tar -xvzf 15994-tuxmania.tar.gz
``` There should be a folder called *Tux-Mania* on your desktop. Play around with the files in there.

When you're done, do this: ```
mv ~/Desktop/Tux-Mania ~/Desktop/randellstheme
sudo cp -R ~/Desktop/randellstheme /usr/share/gdm/themes
```

---

### Post by randell6564 on 2006-11-03
> **aysiu said:**
> Honestly, I think your best bet is to take an existing GDM theme and then just modify the files within it.

That way, you know it works, and you don't have to start from scratch.

Try this: ```
cd ~/Desktop
wget -c http://www.gnome-look.org/content/files/15994-tuxmania.tar.gz
tar -xvzf 15994-tuxmania.tar.gz
``` There should be a folder called *Tux-Mania* on your desktop. Play around with the files in there.

When you're done, do this: ```
mv ~/Desktop/Tux-Mania ~/Desktop/randellstheme
sudo cp -R ~/Desktop/randellstheme /usr/share/gdm/themes
```
I'll give it a shot!  Thanks again!

---

