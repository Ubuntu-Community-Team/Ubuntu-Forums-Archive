---
title: "burning azureus"
date: 2008-01-28
forum: General Help
---

### Post by jl1943 on 2008-01-28
hi, im new with all of this.. i have been using azureus for about 2 months now an i still can not figure out how to burn my downloads onto a disk. if anyone can help me i would really appreciate it because i cant seem to figure it out at all!

---

### Post by cdaringe on 2008-01-28
good day sir! sure, well try and lend some assistance.  first, it largely depends on what kind of media you will be burning.  there are mannny media burning applications out there.  my two preferences are either k3b or gnomebaker.

chances are if you are downloading mp3s and are trying to burn them, you will need some extra plugins. HOWEVER, im assuming that if they are mp3s, you are already able to play them (and thus will not need to gain access to those plugins).

first youll need to find out where your azureus is downloading content to.  mine by default goes to:

/home/cdaringe/.azureus/Documents/Azureus Downloads

note that this is in a hidden folder! what a bummer eh?  when you are in /home/YOUR USER NAME, hold down ctrl and hit h. this will show hidden folders. then you can browse on into your directory.
if your media is not there, open azureus, go to the Tools menu -->Options-->Files
and your media directory should be posted. yahoo. you may already know all of this!

if you dont have a good burning program, go to your main menu, administration, and browse to your synaptic package manager. search for k3b, click it, install it. or type into a terminal:

sudo apt-get install k3b

open up k3b.  you will probably hit 'new audio cd' project.  using the upper half of the k3b window, browse to your directory where you d/l-ed your music or data.  drag songs/etc to the lower half of the window, make sure your blank cd is in your CD drive, and you should be on your way.

hope that all helps. if it was lacking or not what you were really looking for, post back.

---

