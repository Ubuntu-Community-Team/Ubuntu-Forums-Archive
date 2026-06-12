---
title: "Strange problem with my Desktop"
date: 2008-06-10
forum: General Help
---

### Post by gigenieks on 2008-06-10
Hi. I have some weird problem - sometimes I get fully clean Desktop - no icons there or background image, just black screen. :(

It happens occasionaly - sometimes yes, sometimes not.
Basically I restart my computer - and everything is fine after that. But I want to fix this problem now. Question is how? :confused:

See attached image for example!
What is that? Any suggestions how to fix that?

---

### Post by Kinnza on 2008-06-10
could it be some theme you installed or something?

---

### Post by gigenieks on 2008-06-10
I don't think so, I use theme that already is in Ubuntu (not manually installed). I think it is some kernel bug or something like that. As far as I remember this bug appeared after I upgraded to 8.04 (hardy), but I'm not sure.

Edit: I can acces my Desktop files only by going /home/[user]/Desktop

---

### Post by forger on 2008-06-10
> It happens occasionaly - sometimes yes, sometimes not.

Did you mean it happens after upgrading gnome-related stuff? :)

The easy workaround is to press alt-F2 and type: nautilus
That will bring back your desktop and the file manager.

Did you upgrade from feisty/gutsy to hardy? If so, I'd recommend a clean install of hardy, format the root "/" partition and reinstall ubuntu

---

### Post by gigenieks on 2008-06-10
> **forger said:**
> > It happens occasionaly - sometimes yes, sometimes not.

1. Did you mean it happens after upgrading gnome-related stuff? :)

2. The easy workaround is to press alt-F2 and type: nautilus
That will bring back your desktop and the file manager.

3. Did you upgrade from feisty/gutsy to hardy? If so, I'd recommend a clean install of hardy, format the root "/" partition and reinstall ubuntu

1. Hmm, what exactly you mean by that? I have fully updated my system.

2. It doesn't help, besides Nautilus is working fine, the problem is that I don't see my desktop icons & files! :(

3. Yes I upgraded from Gutsy (7.10) to hardy.

---

### Post by gigenieks on 2008-06-10
Any ideas how to fix this?:-k

---

### Post by Habbit on 2008-06-10
It may be another program running in "maximized" mode and obscuring the desktop from you. Check the process list for any suspects.

---

### Post by forger on 2008-06-11
you could type: dmesg
if there was a crash it would print a segfault or something, try it out

---

### Post by Tomatz on 2008-06-11
When it happens try:

killall nautilus

I think nautilus is hanging as nautilus draws the desktop.

Reinstalling nautilus via synaptic may fix the problem ;)

---

