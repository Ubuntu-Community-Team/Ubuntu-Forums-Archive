---
title: "Updating sources.list"
date: 2007-06-25
forum: General Help
---

### Post by toecutter on 2007-06-25
I want to install the new screenlets desktop widgets from here: [http://hendrik.kaju.pri.ee/screenlets/?q=node/5](http://hendrik.kaju.pri.ee/screenlets/?q=node/5)

but the install instructions for Ubuntu say to update my sources.list file


I've previously tried to update the sources.list file (to install other potentially useful/interesting progs) but get a 'not allowed' error every time - I can't even save it with a different file name (like sources.backup). I'm assuming this is because of file permissions but how can I save the file correctly when in the text editor?

---

### Post by merlinus on 2007-06-25
In a terminal:

```

gksudo gedit /etc/apt/sources.list

```-merlin

---

### Post by toecutter on 2007-06-25
Awesome, it worked great :) Thanks!

I was able to edit and save the file, but got this output in the console:
```
(gedit:9372): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

Any idea what that is?

---

### Post by anaconda on 2007-06-25
gksudo still complains unnecessarily. No matter what graphical program you try to run with it..

you could also just use sudo eg:
sudo nano /etc/apt/sources.list

or 
sudo gedit /etc/apt/sources.list

however gksudo is preferred with graphical programs.

---

### Post by merlinus on 2007-06-25
Yes, gksudo does generate useless errors in a terminal, but runs the app anyway.

I have gotten round this by creating a gksudo launcher.

-merlin

---

