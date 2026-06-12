---
title: "[SOLVED] Screenshot of a region drawn by mouse"
date: 2008-04-07
forum: General Help
---

### Post by MountainX on 2008-04-07
I need a gnome app which will allow me to take screen shots of any region drawn with the mouse. I do NOT want something that simply captures either a window or the whole screen. 

The only app I have found, so far, for gnome that supports screen capture for regions is DDM:
[http://www.linux.com/articles/59349](http://www.linux.com/articles/59349)
However, since it will "freeze the entire desktop" I don't want to even try it. I have enough challenges running Hardy beta right now.

I need a decent stable program for capturing screen regions. Any suggestions?

---

### Post by MountainX on 2008-04-07
OK, I found one more option: Gimp.
But that's a very heavy weight option. I'll use it until I find a quick/lightweight app that does the same thing.

---

### Post by SOULRiDER on 2008-04-07
Ksnapshot can do that, but its for KDE so it depends on KDE libs and QT :(

---

### Post by MountainX on 2008-04-07
> **SOULRiDER said:**
> Ksnapshot can do that, but its for KDE so it depends on KDE libs and QT :(

I'm using BasKet already, so it wouldn't be a big deal for me. I didn't notice any issues when installing BasKet (a KDE app) on Ubuntu. Maybe I'll try Ksnapshot. Then I need to begin looking into those ways to make KDE apps look more gnomish.

OT: isn't it too bad that KDE is less stable than gnome? With mono infiltrating gnome, I considered Kubuntu. But I missed Nautilus and the gnome menu layout and other stuff. And the crashes ended my willingness to continue using Kubuntu. I'm back on Ubuntu and I generally like gnome better as a user. But I would like to support KDE because its backers haven't been drinking the Microsoft "koolaid" quite as much.

---

### Post by PurposeOfReason on 2008-04-07
If you are already using compiz, the compiz screenshot plugin can do that.

---

### Post by kerry_s on 2008-04-07
i use scrot
sudo apt-get install scrot

the commands i use:
scrot %T.png  <-standard screen shot
xterm -g 35x1+0+0 -e scrot -cd 5 %T.png  <-counts to 5, then takes
xterm -g 10x0+0+0 -e scrot -sb %T.png  <- click select or drag select

mine are set to keyboard shortcuts.

---

### Post by MountainX on 2008-04-07
> **PurposeOfReason said:**
> If you are already using compiz, the compiz screenshot plugin can do that.

I use compiz. When I looked at the compiz screenshot plugin I didn't see that capability. I must have missed it.

---

### Post by PurposeOfReason on 2008-04-07
> **MountainX said:**
> I use compiz. When I looked at the compiz screenshot plugin I didn't see that capability. I must have missed it.
Just turn it on and use super + mouse drag on button 1 (normal click).

---

### Post by MountainX on 2008-04-07
> **PurposeOfReason said:**
> Just turn it on and use super + mouse drag on button 1 (normal click).
That works! Thanks.

---

### Post by SOULRiDER on 2008-04-08
> **PurposeOfReason said:**
> Just turn it on and use super + mouse drag on button 1 (normal click).

I had no idea compiz could do that, its great to know!

> **MountainX said:**
> 
OT: isn't it too bad that KDE is less stable than gnome? With mono infiltrating gnome, I considered Kubuntu. But I missed Nautilus and the gnome menu layout and other stuff. And the crashes ended my willingness to continue using Kubuntu. I'm back on Ubuntu and I generally like gnome better as a user. But I would like to support KDE because its backers haven't been drinking the Microsoft "koolaid" quite as much.

Ive been using KDE on and off for two years now and I feel its as stable as GNOME.

Also, dont forget to mark the thread as solved. You can do that from the "Thread Options" menu at the top of this thread.

---

