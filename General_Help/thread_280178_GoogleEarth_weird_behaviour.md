---
title: "GoogleEarth weird behaviour"
date: 2006-10-19
forum: General Help
---

### Post by darkghost on 2006-10-19
Hi,
I've noticed a weird problem with GoogleEarth. I've installed it via Automatix and it seemed to work fine, but when I open it the earth is a bit "strange". Maps can't find their places so for instance when i zoom to my town I see maps continually mooving showing me different scale of different nations (India, Uk and randomly so) where I should see the street around my home... What can it be ?

Some specs: 
Kubuntu 6.06 (32bit on AMD64 processor) full up to date
Nvidia driver (from Automatix) for Nvidia Geforce 6200 Turbo cache
1,5 Giga of ram 

What the beep can it be making maps crazy ? (The app loads fine, interface is ok and responsive, just maps are crazy)

Thanks in advance
Andrea

---

### Post by feest on 2006-10-19
well, i guess since google earth uses web streaming (as far as i know) so the problem could be your internet connection.

---

### Post by darkghost on 2006-10-19
Strange, I thought this too, but my cable is working fine (850kb/s) as usual...  maybe their servers...uhmmm

---

### Post by darkghost on 2006-10-19
here is a screenshot of what it happens :D 
It should be showing my town (milano, italy)

---

### Post by sands on 2006-10-19
try searching in google earth supp..
[http://earth.google.com/support](http://earth.google.com/support)

---

### Post by darkghost on 2006-10-19
Thanks Sands! I'll have a look at it

---

### Post by tonyr on 2006-10-19
It's a well known problem with the nvidia drivers. I found some help by
googling 'google earth nvidia' and wound up
[here]("http://www.nvnews.net/vbulletin/showthread.php?t=71756&page=2")
What worked for me was going to the Google Earth Tools->Options 3D View tab, 
and setting Detail Area to Small(256x256).  It isn't perfect, 
but it's way better.

---

### Post by Lord Illidan on 2006-10-19
LOTR Treebeard quote : The world is changing.

---

### Post by thk on 2006-11-14
I see the same thing and I'm on a fast connection. It appears to be a Linux bug. I'm using nvidia-glx.

---

### Post by oakcluster on 2006-11-17
I had the same problem. on both fedora core 5 and Ubuntu Edgy 6.10 on the same hardware.  When I went to install Compiz and the xgl packages on ubuntu (I decided to do away with fedora) the problem went away. Compiz still does not work but googleearth does. 

video card:
eVGA 256-P2-N356-LX GeForce 6500 256MB GDDR2 PCI Express x16 Video Card

I can not recommend a link yet for xgl or compiz since mine is not working, however, I started here:
[http://www.ubuntuforums.org/showthread.php?t=127090]("http://www.ubuntuforums.org/showthread.php?t=127090")
YMMV.

---

### Post by Russty of Oz on 2006-11-17
Are you using Beryl?  I have the same sort of problem when using Beryl, Google Earth wont find places and is very slow moving around, although not as disjointed as yours is.  So if you are using Beryl, try turning it off.  My Google Earth works without a hitch using the standard Gnome or KDE. And I am using nvidia drivers 9629 on an FX 5200.

---

### Post by iamhugeinjapan on 2006-11-17
I have the Nvidia 6200 too. It does the messed up maps thing in Google Earth but is ok under XGL/Compiz/Beryl. I also found that it was fine under the Nvidia 9xxx beta drivers without XGL stuff.

---

### Post by darkghost on 2006-11-18
Thannks for the replies !!
I've lost this post for some time, i still have this problem, and i will try the XGL/Beryl trick to see if it works.
Strange, i think this is related to nvidia6200 , 'cause my laptop with another nvidia card does not have this problem.

Thanks again
Darkghost

---

### Post by darkghost on 2006-11-18
> **Lord Illidan said:**
> LOTR Treebeard quote : The world is changing.

Lol, I love that book/movie. At fast pace I would add :):)

---

