---
title: "SSH entire desktop problem"
date: 2008-06-06
forum: General Help
---

### Post by spanish07 on 2008-06-06
(Skippable text haha)Hey everyone i am a week old in Ubuntu years but i have grown very fond of ssh and decided to do the desktop control thing so in my home network i have been doing so. The problem:
when i do this:


xinit -e ssh -XCT user@server gnome-session -- :1

i get the desktop and its files on my screen just not the current screen more like a blank slate.
     It wouldnt be a problem but since firefox is already open on that computer i cannot open it again on mine. Any help would be appreciated...

---

### Post by spanish07 on 2008-06-06
hm it also happens when i ssh -x i can fire up anything not open and this is a bit more forgiving but i thought it would pull up whatever i want in their screen as well.

---

### Post by briandu on 2008-06-06
May I suggest that u use Putty to connect to your ssh-server. Works like a dream and from Windows too. I use this all the time.

Oh yes, in Windoze use Xming to act as local xserver

---

### Post by spanish07 on 2008-06-06
i mean they both run ubuntu. And i connect quickly and efficiently i just can't bring up the display right(at all).

---

