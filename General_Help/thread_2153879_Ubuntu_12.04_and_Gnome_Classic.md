---
title: "Ubuntu 12.04 and Gnome Classic"
date: 2013-06-12
forum: General Help
---

### Post by carmen2012 on 2013-06-12
I was reading that one way to eliminate Unity was by installing Gnome Classic.

Some of the blogs I was reading said that it was a bit flaky and full of bugs while others said that it was fully supported.  Would anyone know what is the official state of Gnome Classic in Ubuntu 12.04?

Thank you

---

### Post by ahallubuntu on 2013-06-12
~

---

### Post by Frogs Hair on 2013-06-12
Ctrl + Alt + T

```
sudo apt-get install gnome-session-fallback
``` 

or

```
sudo apt-get install xfce4  
``` 
```
sudo apt-get install xfce4-goodies
```

I have both along with Unity. The fall-back session won't be developed, but there are tweaks available and it will be replaced by Gnome Shell extensions.      
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

XFCE can be customized nicely and continues to be developed which is my preference of the two .

---

### Post by ahallubuntu on 2013-06-12
~

---

### Post by Buntu Bunny on 2013-06-12
> **Frogs Hair said:**
> 

<snip>

or

```
sudo apt-get install xfce4  
``` 
```
sudo apt-get install xfce4-goodies
```

+1

There's also a good thread, [12.04 / Precise Classic (No Effects)  Tweaks and tricks]("http://ubuntuforums.org/showthread.php?t=1966370&highlight=classic+tweak"), that may be helpful.

---

### Post by HiImTye on 2013-06-12
I use gnome-classic in Lubuntu, because I prefer it to lxde, it has a memory issue, but it's also in gnome-shell, so it's likely not gnome-classic itself. to fix it, I just```
pkill gnome-panel
```and it frees up the ridiculous amount of RAM it's using (and restarts gnome-panel). usually havento do it every couple of days.

fyi, in gnome-shell the procedure for clearing the memory taken up by gnome-shell is to alt+f2 and then enter```
r
```to restart gnome-shell[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

