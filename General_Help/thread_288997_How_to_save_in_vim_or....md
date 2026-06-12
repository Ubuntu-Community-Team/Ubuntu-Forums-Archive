---
title: "How to save in vim or..."
date: 2006-10-30
forum: General Help
---

### Post by resistdesign on 2006-10-30
I need to know how to save in vim or if there is a better way to edit a file "/etc/X11/gdm/gdm.conf" from terminal mode.

Yes, I was trying to run xgl by default and messed up my gdm.conf, laugh it up!!!

---

### Post by leomcabral on 2006-10-30
to save and exit vim, try:
ESC
then
:wq

---

### Post by bsussman on 2006-10-30
I am on the vi(m) side of the editor arguement, except in integrated dev environments like quanta.

It is a very nice editor.

However, since it has a couple of modes and is text based, it can be tough to remember the commands for the first 15 years.  Try googling fo 'vi cheat sheet' snd you will find many great references.

---

### Post by resistdesign on 2006-10-30
Okay thank you for that it worked, but even though I fixed that file it is still trying to load xgl, any ideas?

--EDIT--
It didn't try to load xgl until I put an entry in gdm.conf

I put:
0=Xgl
and commented out standard:
#0=Standard

So I used vim to undo that and put:
#0=Xgl
and:
0=Standard

But it's acting like I didn't do that.

---

### Post by bsussman on 2006-10-30
> **resistdesign said:**
> Okay thank you for that it worked, but even though I fixed that file it is still trying to load xgl, any ideas?


Congratulations!  You just hijacked your own thread.

So those who look for xgl threads won't see it and us commandliners might not know...

To get a quicker answer, you might want to open another, more appropriately named thread:mrgreen:

---

### Post by bukwirm on 2006-10-30
nano is a somewhat easier-to-learn command line editor.

I prefer vim, though.

---

### Post by resistdesign on 2006-10-30
> **bsussman said:**
> Congratulations!  You just hijacked your own thread.

So those who look for xgl threads won't see it and us commandliners might not know...

To get a quicker answer, you might want to open another, more appropriately named thread:mrgreen:

Yeah, I didn't mean to, I was dealing with a couple of issues and wasn't sure what the problem really was.

---

### Post by tzulberti on 2006-10-30
Should you use vim tutorial for learning all the basics vim commands...
In console: vimtutor

---

