---
title: "Make root changes"
date: 2013-05-18
forum: General Help
---

### Post by mayagrafix on 2013-05-18
I wanted to edit a doc in gedit using the GUI (GNOME files manager) but I could not save because I had no root privileges. In the console I could just sudo or su, but in the GUI what is the proper procedure? log out and come back in as root? there is no "run as root" option in the contextual menu for a temporary fix, so what are my options?

Thanks :)

---

### Post by lisati on 2013-05-18
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Elfy on 2013-05-18
> **mayagrafix said:**
> I wanted to edit a doc in gedit using the GUI (GNOME files manager) but I could not save because I had no root privileges. In the console I could just sudo or su, but in the GUI what is the proper procedure? log out and come back in as root? there is no "run as root" option in the contextual menu for a temporary fix, so what are my options?

Thanks :)

gksudo gedit /file/and/path

[http://askubuntu.com/questions/284306/why-is-gksu-no-longer-installed-by-default-in-13-04](http://askubuntu.com/questions/284306/why-is-gksu-no-longer-installed-by-default-in-13-04)

---

### Post by mayagrafix on 2013-06-18
> **mayagrafix said:**
> I wanted to edit a doc in gedit using the GUI (GNOME files manager) but I could not save because I had no root privileges. In the console I could just sudo or su, but in the GUI what is the proper procedure? log out and come back in as root? there is no "run as root" option in the contextual menu for a temporary fix, so what are my options?)
I found this on another thread: sudo nautilus
It seems to work, I understand it is not recommended to do anything at this level, but is this an answer for my original question?

---

### Post by lisati on 2013-06-18
> **mayagrafix said:**
> I found this on another thread: sudo nautilus
It seems to work, I understand it is not recommended to do anything at this level, but is this an answer for my original question?
It *might* work, but **gksudo nautilus** is better, for the reasons given on the pages already linked to.

---

### Post by HiImTye on 2013-06-18
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
you don't want to use sudo for graphical applications as it may cause permission problems. if you do use it by mistake, then run the command```
sudo chown $USER:$USER $HOME
```

---

### Post by Impavidus on 2013-06-19
Make that last one```
sudo chown **-R** $USER:$USER $HOME
```

---

### Post by HiImTye on 2013-06-19
> **Impavidus said:**
> Make that last one```
sudo chown **-R** $USER:$USER $HOME
```

yeah, that one ;) recursive
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

