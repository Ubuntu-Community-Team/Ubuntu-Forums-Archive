---
title: "new login problem"
date: 2006-07-03
forum: General Help
---

### Post by Polygon on 2006-07-03
OK, since i did not get much help in my other topic i will remake a new one and this time with pictures

When i want to switch to another user without closing all of my programs, i use new login (applications>system tools> new login)

and it works fine, it takes me back to the face browser and all that and i can choose another user to login as.

but, since i usually log out of the computer when im not done with it, i usually leave things like gaim running so i use "new login" to go back to the face browser without closing my programs

BUT: after an extended period of time, when the computer is sitting idle at the face browser after i just used new login to go back to the face browser, when i bring the computer out of its idle state (screensaver or whatever), i get this:

[http://http://img258.imageshack.us/img258/8187/000016je.png]("http://img258.imageshack.us/img258/8187/000016je.png")

it asks me for my password to go back to the face browser in order for someone else to login.

i want to know how to DISABLE that, so that when i bring the computer out of an idle state after leaving it on the face browser after using new login, it just goes back to the face browser and does not ask me for my password or whatever.

any help?

---

### Post by scxtt on 2006-07-03
what happens if you click on "switch user"? -- i'd try it myself, but i've disabled gdm and "new login" doesn't work ...

---

### Post by aysiu on 2006-07-03
Do you have this box unchecked?

---

### Post by Polygon on 2006-07-04
yes that box is unchecked

---

### Post by Matthew Bartram on 2006-07-04
"Switch User" should enable you to get to the face browser without your password. "This box" only affects whether when you are in your user and the screensaver starts it locks the screen. I think when you go "New login" it locks your user.
I presume what is happening, is that after a while, the virtual terminal with your graphical login has closed, putting you back to your (locked) user. I don't know how to stop that happening.

---

### Post by aysiu on 2006-07-04
In KDE, there's a distinction between starting a new session and starting a new one that locks the old one.

I'm not sure if that distinction exists in Gnome or not.

---

### Post by Matthew Bartram on 2006-07-04
I haven't found one anywhere. I think KDE's user switching is more advanced than gnome's. An applet can be added to the panel which makes dealing with multiple users easier in gnome, but I think the KDE one is still better.

---

### Post by Polygon on 2006-07-04
so what you guy's are saying is that this is a gnome limitation and i cant fix it?

---

### Post by aysiu on 2006-07-04
[QUOTE=Polygon]so what you guy's are saying is that this is a gnome limitation and i cant fix it?[/QUOTE]
No. I think we're saying that KDE would offer a way that gives you more control, but I don't believe your Gnome is functioning the way it should be.

---

### Post by Polygon on 2006-07-04
i knew that ghetto way of upgrading from breezy to dapper would cause some problems -.- (i updated by editing my sources.list)

would reinstalling gnome fix it? and if so, exactly what things would i have to reinstall?

---

### Post by Polygon on 2006-07-13
BUMP

ok, the problem is still here.

when i switch user/use new login, it returns to the face browser.

from the face browser, i go idle for a while (like go to bed) and when i come back, i see my screensaver

i move the mouse to come out of screensaver, and it brings me to the screen which i posted a picture of in my first post

switch user will let other users login, but i want to be able to go back to the face browser so if im not around, my family can restart the computer instead of holding down the power button and shutting it off that way.

any other help? thanks!

---

