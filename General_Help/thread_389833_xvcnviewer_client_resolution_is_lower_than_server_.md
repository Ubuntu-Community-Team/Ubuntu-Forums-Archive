---
title: "xvcnviewer: client resolution is lower than server resolution"
date: 2007-03-21
forum: General Help
---

### Post by littlegreenman on 2007-03-21
Hello,

I am using xvncviewer to log in to a xp machine. The problem is that the resolution of the xp machine is higher than the resolution of the client kubuntu machine.

Is there a way to configure vnc in order for the client's resolution override the server's resolution? 

Thank you for all your help.
Littlegreenman

---

### Post by jkarlsen on 2007-03-22
is searching for the same answer... my resolution is higher on my desktop computer. and if i scroll the window in vnc, i can't scroll back to see the rest of the screen :S

anyone know?

---

### Post by littlegreenman on 2007-03-23
Let's hope somebody answers.

---

### Post by mayfer on 2007-03-23
yep, i have the exact same problem. after i scroll once, i can't scroll anymore.

i'd be glad if someone could help

---

### Post by polki@mac.com on 2007-03-23
Same here. But i found that I could go up again using right-click. Hmmmm...
Right-click in the scroll bar that is.

---

### Post by MetalMusicAddict on 2007-03-23
On older versions of RealVNC for windows you could scale-down the screen from the server when viewing on a client. It doesnt look like you can do this on current versions of RealVNC or xvncviewer.

So atm the answer to this question looks to be no. Ive asked before and even started my own thread about it. :(

Look [HERE]("http://www.fifi.org/cgi-bin/man2html/usr/X11R6/man/man1/xvncviewer.1x.gz") for xvncviewer options.

---

### Post by c.los on 2007-05-04
as for the scroll bar problem, i am having that also - if you open up xvncviewer full screen then you dont need the scroll bars and your screen just moves with your mouse...'

try...

xvncviewer -full


------------

im also trying to figure out that other question. I got dual monitors on my work comp, but of course only one on my laptop. its fine if i could only use one but it actually lets me scroll thru both and i want 1280 * 800 when im remote from the lappy but back to 1280 *  1024 local

you can always change it while your remoted in.. but then you have to change it back when you get back on locally

---

