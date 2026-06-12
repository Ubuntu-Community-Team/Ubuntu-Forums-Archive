---
title: "Deja-dup keeps asking me for my password every few minutes"
date: 2013-11-26
forum: General Help
---

### Post by marinecomm on 2013-11-26
Every time I run deja-dup it repeatedly asks me for my password every few mintues. Also, in the 'details' screen it just shows the same files and doesn't seem to scan any new ones. Any thoughts or ideas? I'm running Xubuntu 12.04 64-bit.

---

### Post by bashiergui on 2013-11-26
The resolution in this thread should work for you, too.
[http://askubuntu.com/questions/130674/how-do-i-open-deja-dup-as-root](http://askubuntu.com/questions/130674/how-do-i-open-deja-dup-as-root)

---

### Post by marinecomm on 2013-11-26
Ok, I followed the directions in the thread but now deja-dup asks me for my password ever several seconds instead of minutes.

---

### Post by bashiergui on 2013-11-27
That's pretty much the opposite of what you wanted. :-/

You could try gksudo instead of gksu. If I remember correctly that should ask you for your password in the terminal and then launch deja-dup as a sudo user. I don't know why it would ask for your password henceforth.

---

### Post by bashiergui on 2013-11-27
Is it asking for your sudo passwor or for your backup password? 
My instructions assumed it was the sudo password.

This is an easy to read overview of deja dup which might answer some of your questions. 
[http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/](http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/)

---

