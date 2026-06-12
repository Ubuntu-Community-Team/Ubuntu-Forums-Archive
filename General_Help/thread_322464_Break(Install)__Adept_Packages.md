---
title: "Break(Install)  Adept Packages"
date: 2006-12-20
forum: General Help
---

### Post by hokah on 2006-12-20
Hi

I have problem with Adept, I have finally managed to add repos to my sources.list without errors with GPG keys, but now it is not much more easier.

1) Trying to install samba all what I get is Break (Install) just cant install, but I cant read why ?
2) Automatix - same problem
3) Stellarium I have installed I have even icon in my Programs Menu but after i click the icon something is loading and then nothing ... I dont know whats is wrong ?

Is there any way to make it easier ?

regards 
Peter on Kubuntu 6.06

---

### Post by hokah on 2006-12-21
I have solved problem using terminal, I have recieved information about installed bad versions of some dependencies, all what I need to do is to remove this dependencies and install package again.

regards
Peter

---

### Post by hikaricore on 2006-12-21
Aye remember terminal is your friend when it comes to application diagnostics :)

Were you able to get stellarium working properly as well?

---

### Post by hokah on 2006-12-21
Unfortunatly not ;-(
Under terminal ofcours ;-) I saw that there is problem with GLX (as I renember) its strange as I have checked x.configuration file and there is Load = GLX so it sholud be loaded.

---

### Post by hikaricore on 2006-12-21
Is direct rendering enabled on your system?

```
 glxinfo | grep rendering 
```

If this returns no, you'll need to search around for info on configuring your video drivers.

This is a must if you plan on doing anything besides surfing and playing card games.  hehe

---

### Post by hokah on 2006-12-21
piotras@Dziubeks-desktop:~$ glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by hikaricore on 2006-12-21
What type of video card do you have?  that might be a good place to start with this one hehe

---

### Post by hokah on 2006-12-22
Heh acctually you are right
I have G Force FX 5200 and today Im swithing to UBUNTU 6.10 I think my problems are related to KUBUNTU so I hope I will have easier life with supported version of OS.

---

