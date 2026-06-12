---
title: "Gimp crashes"
date: 2005-07-29
forum: General Help
---

### Post by jarg on 2005-07-29
No matter what I am doing when ever I open gimp my screen goes black and I have to restart my computer to do anything. I am opening gimp from my "applications" menu. 

Anyone else having this problem. Any clue why it is crashing?

---

### Post by coolclassic on 2005-07-29
How did you install it?

---

### Post by jarg on 2005-07-29
[QUOTE=coolclassic]How did you install it?[/QUOTE]

It came on my disk with ubuntu

---

### Post by jeremy on 2005-07-30
You could try renaming your 
/home/YOUR_USERNAME/.gimp-2.2
folder (NOTE it is a 'hidden' folder) to something else, then try to start Gimp.

---

### Post by coolclassic on 2005-07-30
Two options

1. Use synaptic and fix broken packages

2. Using synaptic reinstall gimp

---

### Post by jeremy on 2005-07-31
So, have you got anywhere? I recommend that you try my suggestion first (it is easily reversible).

If you use apt or synaptic to reinstall, make sure you deinstall and purge it completely before making a fresh install.

---

### Post by jarg on 2005-07-31
[QUOTE=jeremy]So, have you got anywhere? I recommend that you try my suggestion first (it is easily reversible).

If you use apt or synaptic to reinstall, make sure you deinstall and purge it completely before making a fresh install.[/QUOTE]
 I'm working on it, I was besy, I let you know if it doesn't work.

---

### Post by j0e on 2005-07-31
You could try running GIMP from the command line. And, if necessary, direct any output to a file - just to see if it tells you anything before the screen goes black.

---

