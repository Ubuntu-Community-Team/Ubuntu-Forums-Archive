---
title: "gnome-panel continuosly crashes"
date: 2006-12-06
forum: General Help
---

### Post by ghepardo on 2006-12-06
I cant use more gnome. Gnome panel crashes continuosly, and it saves the file attached to this post. I cant use gdm more because always gnome panel crashes.

What can I do?

---

### Post by ghepardo on 2006-12-06
Help plz.

I reinstalled Ubuntu from scratch. I formatted both root and swap partition, I didn't formatted the home one because I have files I need there, but the problem is unsolved. What can I do? Plz help.

---

### Post by ghepardo on 2006-12-06
Up

---

### Post by ghepardo on 2006-12-06
up

---

### Post by larvar on 2006-12-06
Well, I have suddenly the same prob, did u do anything before, that could cause this prob. I was installing crossover with photoshop, successfully. And mountISO unsuccessfully. I found this: [http://bugzilla.gnome.org/show_bug.cgi?id=317984](http://bugzilla.gnome.org/show_bug.cgi?id=317984)

so we are not the first:(

---

### Post by ghepardo on 2006-12-07
T_T. I also reinstalled all the system (I just didn't formatted the home partition) and the problem is still there...so in my opinion is caused by some file in the home folder...

---

### Post by ghepardo on 2006-12-07
This bug is known, and they say is fixed, but I can't find the fix here:
[https://launchpad.net/distros/ubuntu/+source/gtk+2.0/+bug/66189](https://launchpad.net/distros/ubuntu/+source/gtk+2.0/+bug/66189)

where can I find the fix?! Someone knows how launchpad works!?

---

### Post by robinl on 2006-12-07
Maybe an update will help since it is marked fixed upstream which means the fixed version is available from update? Also make sure your system is stable (ie no over-over-clocking etc.), gnome panel crashing is one of the first thing happens when I boot into Linux with the wrong memory frequency (Windows just give me a blue screen).

---

### Post by larvar on 2006-12-07
did apt-get update today and got some gnomefiles and the prob is gone!

---

### Post by ghepardo on 2006-12-07
for me apt-get update didn't solved. I had to remove this folder from my home: .recently-used.xbel 
and now it works again.

---

### Post by rupienze on 2007-01-14
yes problem is recently-used.xbel

i used this. its working 

sudo rm .recently-used.xbel
sudo rm -r -f ~/.gnome*.gconf*
sudo rm -r -f ~/.gtkrc*
ctrl alt backspace
login again

_ ruPi _

---

