---
title: "Looking for dash-like software for Xubuntu"
date: 2014-12-13
forum: General Help
---

### Post by markodd on 2014-12-13
Hey there,

I'm looking for a software like Dash for Xubuntu. What I want is something that allows me to search for files, folders and installed software. I'd like to be able to set a keyboard shortcut to "open" said software (for example, clicking on the windows key opens dash).

Does something like that exist?

---

### Post by Frogs Hair on 2014-12-13
Besides the wisker menu and app finder( native to Xubuntu) I don't know of any . Synapse lost support after 13.10 and  was my preference  when using XFCE. Gnome Do came up in my search though I don't know if it works with XFCE .

---

### Post by markodd on 2014-12-13
> **Frogs Hair said:**
> Besides the wisker menu and app finder( native to Xubuntu) I don't know of any . Synapse lost support after 13.10 and  was my preference  when using XFCE. Gnome Do came up in my search though I don't know if it works with XFCE .

The whisker menu does not allow to search for folders and files, does it?

Also, is there a way to set a keyboard shortcut to open the whisker menu?

---

### Post by Toz on 2014-12-13
There is also [xfdashboard]("http://www.webupd8.org/2014/07/xfdashboard-gnome-shell-like-dashboard-xfce-xubuntu.html") which is kind of like the dash in Unity or Gnome shell activities. However, you can't search for files and folders with it either.

---

### Post by Dennis N on 2014-12-13
> **markodd said:**
> The whisker menu does not allow to search for folders and files, does it?

Also, is there a way to set a keyboard shortcut to open the whisker menu?

Search for files: **Accessories > Catfish File Search**

Whisker Menu keyboard shortcut: **Ctrl + Esc**

---

### Post by markodd on 2014-12-13
> **Dennis N said:**
> Search for files: **Accessories > Catfish File Search**

Whisker Menu keyboard shortcut: **Ctrl + Esc**

Thank you very much Dennis N!

---

### Post by ajgreeny on 2014-12-14
> **Dennis N said:**
> Search for files: **Accessories > Catfish File Search**

Whisker Menu keyboard shortcut: **Ctrl + Esc**
This is not working for me; I get a right click context menu as if on the desktop instead of whisker menu.  Where is the setting for whisker menu showing with this key shortcut?

I have looked in the Window-manager tab of xfce-settings-manager, and in keyboard shortcuts but it's not in either.

---

### Post by CantankRus on 2014-12-14
It's not dash-like but if you want a keyboard way to quickly launch applications,
find files and other functions through plugins, try **kupfer**.
I use it across a number of desktop environments.

Here's a [**_[COLOR="#B22222"]youtube video[/COLOR]_**]("https://www.youtube.com/watch?v=TG4L-hLsoCk"). It's a few years old but kupfer is pretty much the same just looks better.

---

### Post by CaptainMark on 2014-12-14
You can set any keyboard shortcut for whisker menu, just use the normal xfce keyboard shortcut section and map the command xfce4-popup-whiskermenu to a key. I'm away from my computer right now so if someone could please verify the correct command, tab completion in a normal terminal will do, I have it mapped to the windows/meta key on its own to mimic dash behaviour.

---

### Post by ajgreeny on 2014-12-14
> **CaptainMark said:**
> You can set any keyboard shortcut for whisker menu, just use the normal xfce keyboard shortcut section and map the command xfce4-popup-whiskermenu to a key. I'm away from my computer right now so if someone could please verify the correct command, tab completion in a normal terminal will do, I have it mapped to the windows/meta key on its own to mimic dash behaviour.
Thank you so much CaptainMark for that command, which was the thing I  could not find anywhere; I didn't even think to look for something with  whisker in the name in /usr/bin, silly me!

I can confirm that your command mentioned above works fine in 14.04.
I have it set to Winkey+W, just what I wanted, rather than Winkey alone as that it one of the two keys of many other shortcuts I use a lot.

---

