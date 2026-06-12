---
title: "Problms login in"
date: 2008-04-09
forum: General Help
---

### Post by K.Morgan on 2008-04-09
Hi, I have installed Ubuntu 7.10 on my computer and everything went fine.  At the end of the installation i rebooted and was then given a login screen.  I have entered the username and password exactly as i stated during the installation but i can't login at all.  Does anybody know why this is?

I even deleted the installation and re-installed thinking i did something wrong, but again the same problem exist and can't login no matter what i do.


Kristian

---

### Post by jeremy on 2008-04-09
Are you given any feedback, or does nothing happen at all?

---

### Post by K.Morgan on 2008-04-09
Hi Jeremy, It keeps telling me that i have entered an incorrect username or password, but the username and password i'm entering is definitely right.


Kristian

---

### Post by jeremy on 2008-04-09
I would try checking the case, both username and password are case-sensitive (accidently pressed CapsLock key???). Good luck.

---

### Post by K.Morgan on 2008-04-09
Nope, caps lock not on, username and password are all lower case, it just keeps telling me that it's wrong.

Completely lost

Kristian

---

### Post by hotswap on 2008-04-10
I am having the exact same issue. I had set my username and password to something that I use for something else and it just comes back Login incorrect and prompts me.

---

### Post by puffy1980 on 2008-04-13
Its a problem with the installiation. I have the same problem. If you boot to fail safe, Ubuntu logs in as root at terminal. Type startx and it should let you in. 
It seems in the install the user section wasnt installed correctly, because once in, if you click on users, even tho your logged in as root, it says you dont have the correct privileges.
Find another install disc and try again. Im waiting untill 8.04 comes out, then I'll just re-install with that.
Either that or just keep logging in via failsafe.

---

### Post by bapoumba on 2008-04-13
Did you install the alternate version (in that case, the user created is "oem" and the password the one you specified during the install).

---

