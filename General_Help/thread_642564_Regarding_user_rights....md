---
title: "Regarding user rights..."
date: 2007-12-16
forum: General Help
---

### Post by Moonfrost on 2007-12-16
I intalled a program which is located at my home folder...what I want to do is open it to check something but tells me I don't have the rights since I'm not root...is there a way to open it without having to login as root? thanks in advance...

---

### Post by LaRoza on 2007-12-16
Run "sudo" before the command name.

(You can't log in as root, by default)

How did you install this program?

---

### Post by Moonfrost on 2007-12-16
> **LaRoza said:**
> Run "sudo" before the command name.

(You can't log in as root, by default)

How did you install this program?

I can log out and log in as root without me changing everything...but of course, in root that file won't be there...anyway, I installed via a command line because it was a .run file, after that a GUI appears kinda like Windows programs and welcomes me and all that and choose where I want to install which by the way I left as default...it's Unreal Tournament 2004 demo by the way...

---

### Post by Lostincyberspace on 2007-12-16
It looks like you aren't going to the users home folder in root. it would not be the default home folder. First find the file it will be in /home/user name/what ever else/  then right click on the program and set the permissions to be the user you want.

---

### Post by scizzo on 2007-12-16
Did you install the game using:

# sudo sh file.run

Or something simular to that?

---

