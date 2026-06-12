---
title: "windows inside ubuntu, seperate computers"
date: 2007-05-26
forum: General Help
---

### Post by mailbox on 2007-05-26
Alright, here's my issue. I have an app, Valve's Hammer editor, that just /will not/ run on Ubuntu. It's the only app so far that I can't run or replace, and I do (did) use it frequently, so I went and installed Windows 2000 on a second computer (named mallet) soley for this one application.
My question now is, how do I get the output from mallet onto my primary machine (iridium)?
I was thinking I could run some s-video cable from mallet's tv-out into a pci tv-tuner on iridium, but from there i'm unsure on how to make that input show up in an X window.
There has to be a better way of doing this, though. That doesn't sound like a very elegant solution, considering that every time I'd go into that window, I'd have to hit a KVM switch.
VMWare won't do it either, because I'm going to be working with a 3D app, DX accellerated.
Both these machines are networked through a 1gbps switch, and I can move them right next to each other if need be. Anyone have any suggestions/ideas/soluitions?

Sorry for the crappy title, too.

---

### Post by mailbox on 2007-05-26
anyone?

---

### Post by mdurham on 2007-05-26
take a look at vnc (I use xtightvncviewer). This allows you to run one computer from another. I 'think' that's what you want.
Cheers, Mike

---

