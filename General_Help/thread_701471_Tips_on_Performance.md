---
title: "Tips on Performance"
date: 2008-02-19
forum: General Help
---

### Post by lamcro on 2008-02-19
I have an HP Pavilion ze5700 with an Ubuntu 7.10 partition and some 256 MB of RAM.

My intentions with this computer are web-work on open Wi-Fi's and some OpenOffice use.  No games, music or DVD movies.

What should I do to improve it's performance (other than buying more RAM)?
  - Any internal services I could eliminate?

What should I do to improve security?
  - Will it affect performance?

Thanks.

---

### Post by pointone on 2008-02-19
A more lightweight desktop environment like Xfce or Fluxbox would certainly help. Try installing xubuntu-desktop and give it a spin.

---

### Post by lamcro on 2008-02-19
I had in mind using one of those.
Should I download the whole image or just download it using apt-get?

---

### Post by pointone on 2008-02-19
You can try it out by just installing xubuntu-desktop and starting an Xfce session from GDM. If you like it, you can reinstall using the image for a "cleaner" system (i.e., none of the non-Xubuntu stuff lying around), but there's probably not much difference between an Xubuntu install and an Ubuntu install + xubuntu-desktop.

---

### Post by RedSquirrel on 2008-02-19
Using a window manager such as Fluxbox, Openbox, IceWm, etc. instead of GNOME would help a great deal. After you install a window manager, you can find it in the Sessions menu of your login screen.

If you want a really light and fast system, try a minimal installation:

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)


Edit: K.Mandla's blog has a guide for speed tips... [http://kmandla.wordpress.com](http://kmandla.wordpress.com)

---

### Post by lamcro on 2008-02-26
OK, I tried Xubuntu-desktop (through apt-get) and found not much difference, so I will stick with ubuntu for now.
I would like to try eliminating as many internal, unnecessary applications that are launched when the computer is started.  I already eliminated the scheduling and printing services.

Any other apps I can kill?

---

### Post by eriqjaffe on 2008-02-26
I have to second RedSquirrel's recommendation of a minimal installation with a Window Manager- it's far easier to add things that you need than to remove things that you don't.

---

### Post by thedaemon on 2008-02-26
Openbox or similar is the way to go. IceWM, etc. There are a handful of nice WM. Using firefox is also a no no.

---

