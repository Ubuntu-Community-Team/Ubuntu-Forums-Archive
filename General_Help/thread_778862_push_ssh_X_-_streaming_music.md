---
title: "push ssh X - streaming music"
date: 2008-05-02
forum: General Help
---

### Post by Pat L.I. on 2008-05-02
Hello, Sorry for the confusing title.

I have laptop A that i use regularly (ubuntu 8.04)
I have laptop B hooked up to speakers which I only use to SSH into for file storage and to play music etc (ubuntu 8.04)

I understand how to ssh from laptop A -> B and forward X in order to start up Amarok and begin playing music which resides on laptop B through the speakers on laptop B, but presenting the GUI on laptop A. (Tongue Twister) still with me? 

is it possible to SSH A-> B , and play music that resides on laptop A through the speakers on laptop B. I guess this would be more like push streaming!

I will try to ask again if im not making sense, its early!!
thanks in advance!

---

### Post by Pat L.I. on 2008-05-02
is my question understood? does anyone know what im trying to do!!!!?

---

### Post by jjk7288 on 2008-05-02
It'd probably be kind of slow, but you'd have to share your music on laptop A, then in Amarok you want to open the mp3s that are in that share. A symlink in your music folder on laptop B to link to the share on A would help navigation-wise. (type "man ln" in the terminal). 

Hope that helps.

Quick note: Make sure that for the music on laptop A that other users have at least read access to your music so that it can be shared properly.

---

