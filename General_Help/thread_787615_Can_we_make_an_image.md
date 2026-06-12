---
title: "Can we make an image?"
date: 2008-05-09
forum: General Help
---

### Post by Alex&amp;Linux on 2008-05-09
Hey all,

I finally have EVERYTHING running perfectly on my 13" intel macbook -including the elusive "suspend to RAM" (this seems to work for no reason)

A couple of questions:

1. Can I make an image of everything I have so that I can re-install Ubuntu in its current state at a later time (for example, if I try an upgrade which breaks something, and I want to go back to this state)?

2. Suspend is one of the last two pieces of the puzzle -with it, Ubuntu is just one step away from being better than OS X on my mac (battery life is the other item which is not fully addressed). Does anyone know how to figure out why it is working now? Perhaps there is information that can show exactly what I need to get it working in the future, especially if #1 cant be accomplished?

---

### Post by tamoneya on 2008-05-09
for making a CD image you should look into [remastersys]("http://howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys").  It allows you to make custom ISO for your install. 

As for battery I am not quite sure what you are trying to solve.  What isnt working.  Is it just that you get less battery life in ubuntu than in OSX?

---

### Post by logos34 on 2008-05-09
if you use remastersys, though, you have to go through reinstall.

An easier method (which I use) is to simply make an image of root partition with Partimage before any major change:

[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)

Store the compressed .img file on another partition (or better yet on another hard disk or DVD if it will fit)

If you ever get in trouble fire up the ubu live cd and restore it

---

