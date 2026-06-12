---
title: "Window Decorator Missing on One Account"
date: 2008-05-18
forum: General Help
---

### Post by wyth on 2008-05-18
I've been searching this one out for some time now, with no luck.  So I throw it out to you all.

On our desktop computer, we have two accounts, one for me and one for my wife.  Compiz is running on both.  It's perfectly fine on my account, but my wife's account always starts with no gtk-window-decorator running.  

We've tried it with gtk-window-decorator --replace at start, and without (both in Gconf and ccsm).  No matter what, it always starts without the decorator.  Reloading the window manager brings the decorator up.  

The card is an Nvidia 8600GT, and is set with indirect rendering and loose binding.  Again, it works fine under my account.

So what exactly am I missing here?  Should I nix her account and start fresh, or is there an easy fix?

---

### Post by wyth on 2008-05-19
up

---

### Post by wyth on 2008-05-19
up again -- lets try the afternoon crowd.

---

### Post by wyth on 2008-05-19
c'mon folks, I hope you have something to say.  I can't come reset the window decorator every time my wife logs into her account -- what might be causing this, and what's the obvious fix that I'm missing?

---

### Post by wyth on 2008-05-21
72 hours later, and no one had a thing to say.

Well, Ubuntuers, I did it myself; nixing the account and building it again did the trick.

---

