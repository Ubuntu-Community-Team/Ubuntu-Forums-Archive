---
title: "Live CD Help"
date: 2007-01-17
forum: General Help
---

### Post by everlight on 2007-01-17
I've wanted to try out Linux for a while now and several people recommended that I try Ubuntu. Ive read many good things about it so I thought "Why not?". So I pop in the CD and I choose the first option, to Start Ubuntu. Its loading and then it comes to a blue screen with a gray box that says "failed to load x server"....."do you want to view diagnostics". I chose yes and it said "Fatal server error: no screens found"
I searched first and couldnt find anything. Any help?

---

### Post by taurus on 2007-01-17
What's the spec of your computer, especially the graphic card?  Can you get to a console by pressing <Ctrl><Alt>F2.  If you can, run this command to see if it can reconfigure your X again.

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

