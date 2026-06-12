---
title: "Compiz + Fullscreen game problem."
date: 2008-05-26
forum: General Help
---

### Post by Cygoku on 2008-05-26
Hi folks, 
     I am using a 7 to 8 emulators and each time I use fullscreen when compiz is activated, everything is transparent and I can see the desktop.

Where the hell can I disable that WITHOUT disabling Compiz?

Cygoku

---

### Post by Forlong on 2008-05-26
What version of Ubuntu are you using?

Also: what are those "emulators" you are referring to exactly?

---

### Post by Cygoku on 2008-05-26
> **Forlong said:**
> What version of Ubuntu are you using?

Also: what are those "emulators" you are referring to exactly?I am using Ubuntu Hardy Heron 8.04 with the default Compiz installed.  

The emulators I am referring to are, sdlmame, gens, mupen64plus & gfceu.

Cygoku

---

### Post by Forlong on 2008-05-26
OK, in case you don't have it already, install ccsm: ```
sudo apt-get install compizconfig-settings-manager
```

Afterwards, run it like this:
```
ccsm
```
and click on **General Options**, there you go to the **Opacity Settings** tab.

Now run any of the applications you'd like to keep opaque.

Afterwards, click on **New** under **Window Opacities**.
In the popup, make sure **Opacity window values** is set to **100**.
Then click on **+** and in the following popup on **Grab** -- your mouse-cursor should've turned into a cross-hair now.
Finally, click on the application you ran earlier.


Repeat those steps for all the other applications.

---

### Post by Cygoku on 2008-05-26
Thank you, this worked like +100 resist fire charm.

Cygoku

---

