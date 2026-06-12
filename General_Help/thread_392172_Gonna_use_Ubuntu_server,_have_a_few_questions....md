---
title: "Gonna use Ubuntu server, have a few questions..."
date: 2007-03-24
forum: General Help
---

### Post by .hybrid on 2007-03-24
Hey.

I'm going to be using Ubuntu webserver 6.06, because it has the easy LAMP installation, so with a few other things, the webserver should be ready to go. In addition to it being a webserver, I'd also like to have it as a desktop for normal computer things. I'd like to use KDE. What package would give me all the things one would need for a desktop computer?

Also, is the a network connection client that I could download that would allow me to share files with my XP computer? In Freespire for example, the network connection client just worked, no passwords, no typing, all I had to do was double click on the icon, and that was it. I put stuff in the XP shared folder, I recieved it in the Freespire equivilent, and vice versa.

---

### Post by jeffathehutt on 2007-03-24
The easiest way to get kde installed is to use the command:
```
sudo aptitude install kubuntu-desktop
```

For sharing files with a windows computer, you should look into samba.  I don't use kde so I'm not sure how you configure samba from there, but in gnome there is a menu item in System->Administration->Shared Folders

---

### Post by depele on 2007-03-24
kde ! simply remote locations... (or network location.) 
I am now under windows .. (school ****)


the rest should speak for itself...


grtz...

---

### Post by fharczuk on 2007-03-24
I just installed the server version and want the graphical interface.  How do I boot with that?  I am a newbie but experienced with windozes.

tia

---

### Post by jeffathehutt on 2007-03-24
If you want the gnome interface (Ubuntu), just install the ubuntu-desktop package:
```
sudo aptitude install ubuntu-desktop
```

For the kde interface (Kubuntu):
```
sudo aptitude install kubuntu-desktop
```

Then reboot and it should load the graphical interface.

---

