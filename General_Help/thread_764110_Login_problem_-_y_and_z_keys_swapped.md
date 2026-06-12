---
title: "Login problem - y and z keys swapped"
date: 2008-04-23
forum: General Help
---

### Post by todivefor on 2008-04-23
I posted this in the Apple forum, but got no response, so am hoping for a better result here.

I am new to Ubuntu and in the early stages of learning.  On the login screen, my y and z keys are interchanged. My password has a "z" in it, so I have to type "y" for my password to take. Any ideas?

I am running Ubuntu 7.10 on an alum. iMac.

---

### Post by tacutu on 2008-04-24
What keyboard layout are you using?
Some keyboard layouts (German, for instance) have the z and y keys swapped. Maybe that's your problem?

---

### Post by todivefor on 2008-04-24
tacutu,

I think that is my problem.  How do I tell?  I changed all mu user layouts to USA and resynced my passwords.  This did not work for my login.

---

### Post by tacutu on 2008-04-25
Hmm, I think you need to set-up the keyboard layout in /etc/X11/xorg.conf for this:

sudo gedit /etc/X11/xorg.conf

and change the german layout to us.

---

### Post by todivefor on 2008-04-25
That did it.  Thank you.

---

