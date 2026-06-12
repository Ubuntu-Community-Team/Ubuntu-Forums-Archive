---
title: "Adjust X11 Hz"
date: 2005-05-10
forum: General Help
---

### Post by TomSawyer on 2005-05-10
Running Ubuntu 4.10 and when I did the live disk, the resolution of the desktop looked great. 

Once I installed on my laptop (Averatec), it doesn't look so great.  Once installed, the screen resolution is: 

1024x768 
60Hz 

The live disk has it as 

1024x768 
76Hz 

How do I adjust the Hz from 60 to 76?

Looking at XF86Config-4 file, the HorizSync has a range of 28-49 and a VertRefresh rate of 43-72, can I adjust these?

---

### Post by Zelut on 2005-05-10
Be careful before changing numbers like that on a hunch.  I once burned out a VGA card by trying to hack the refresh rates like that.

I'm not at my ubuntu box now otherwise I'd post a method on changing that.  I'll try to remember when I get home.  Just wanted to point out that you can really cause problems by guessing here.

---

### Post by TomSawyer on 2005-05-10
[QUOTE=kuyaedz]Be careful before changing numbers like that on a hunch.  I once burned out a VGA card by trying to hack the refresh rates like that.

I'm not at my ubuntu box now otherwise I'd post a method on changing that.  I'll try to remember when I get home.  Just wanted to point out that you can really cause problems by guessing here.[/QUOTE]

Yes I know that playing with X can have big problems. 

What is suprising is why the live disk had the refresh rates right and then I did the install and it went to hell.

---

