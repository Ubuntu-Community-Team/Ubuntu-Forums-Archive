---
title: "Home network, iTunes Music share, Ubuntu"
date: 2007-06-02
forum: General Help
---

### Post by jrattner on 2007-06-02
Currently I live in a house with two other guys who use windows.  On their computers they have a vast amount of music in iTunes.  Is it possible for me to access their music shares from Ubuntu and play some of their music?

---

### Post by dave-5B on 2007-06-03
you can access any shared folders on their pc directly by looking in places > network

if you dont see anything you need to :
sudo apt-get install samba smbfs

so if your friends have the folders with all their music shared you can point your music player  of choice at them.

as for directly accessing the iTunes library, possible but dont know how

---

### Post by jadeshade on 2007-07-18
The music player Exaile (and I believe amarok, too) both can access itunes shares (the daap protocol).  If you want to use Exaile (uses gtk/ better integrates with the normal ubuntu desktop), then check [http://syzygy42.tuxfamily.org/dists/feisty/exaile-svn/](http://syzygy42.tuxfamily.org/dists/feisty/exaile-svn/) since the exaile version in the ubuntu repos is out of date.  I haven't used amarok in a while, but I'm sure one will pop up and tell you how to configure it.

---

### Post by kostkon on 2007-07-18
I'm pretty sure the version of *Rhythmbox* in *Ubuntu Feisty* can access *iTunes *shares; and the plugin (DAAP) is already activated, although you can go to the *Plugins* option and configure it, if you want to share your own music. Nevertheless, I don't know if this works in Ubuntu Edgy or Dapper.

Which version of Ubuntu do you have?

---

### Post by reacocard on 2007-07-18
If they use iTunes 7, you're out of luck, no FOSS music player can connect to an iTunes 7 share. Rhythmbox, Amarok and Exaile all do iTunes 6 and earlier shares though.

---

### Post by strabes on 2007-07-18
If they use iTunes 7 the easiest (only?) thing to do would be to have them share the actual **folder** on their computers where their music is located. At least that way you could access it with samba.

---

### Post by daybreaker on 2007-08-27
Thanks reacocard, thats the problem I was having. :-P  Stupid iTunes 7.

---

