---
title: "Login problem"
date: 2004-11-17
forum: General Help
---

### Post by andbert on 2004-11-17
The following message occurs when i try to login.

Your session only lasted less than 10 sec. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one off the failsafe sessions to see if you can fix the problem.

Im able to start the terminal, but not Gnome. 

Any input on how to correct this?

---

### Post by duff on 2004-11-17
[QUOTE=andbert]The following message occurs when i try to login.

Your session only lasted less than 10 sec. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one off the failsafe sessions to see if you can fix the problem.

Im able to start the terminal, but not Gnome. 

Any input on how to correct this?[/QUOTE]

have you checked your diskspace with `df` or tried logging into one of the failsafe sessions, as is suggested?

---

### Post by andbert on 2004-11-17
Ive tried failsafe terminal.....
But Gnome wont work.

---

### Post by andbert on 2004-11-17
the error file shows:

** (gnome-session: 4565) : WARNING**: Unable to read ICE authority file:
/home/andreas/.ICEauthority

how do i correct this?

---

### Post by jdong on 2004-11-17
sudo rm -rf /home/[user]/.ICEauthority

---

### Post by andbert on 2004-11-17
Thanks alot it worked :)

---

### Post by easy_target on 2004-11-25
Hey, I've had the same problem and seems to happen when you login as root and startx (saw it in a Fedora thread in Linuxquestions). Why does that happen? Is it a bug? Sould it be submitted to teh developers so they can reproduce it and fix it?

Thanks!

---

