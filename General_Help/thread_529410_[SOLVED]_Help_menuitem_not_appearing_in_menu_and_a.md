---
title: "[SOLVED] Help menuitem not appearing in menu and alacarte but app.desktop present"
date: 2007-08-19
forum: General Help
---

### Post by frafu on 2007-08-19
Hello, 

I have deleted a menuitem from an application with alacarte (Main Menu) and after reinstalling that application its menuitem does not reappear anymore even though its application.desktop file is available under /usr/share/applications with rw-r--r-- rights.

The menuitem of that application does not even show up in alacarte. Is this normal behaviour or is something broken on my system? Does alacarte remember what has been deleted? If it is normal, how can I make alacarte show all installed menuitems? 

I know that I can create a menuentry with alacarte. But that is not the point here.

Thanks in advance. 

Francesco

---

### Post by jnorthr on 2007-08-19
some packages may require you to explicitly declare you want menu entrys, is it possible your package has such a choice and it was missed on this reload ?

---

### Post by frafu on 2007-08-19
@jnorthr

First, thanks for your reply. 

I don't think that it is what you suggest. In fact, I installed and removed the package quite often. Each time I removed it, the menuitems were gone. After reinstallation, the menuitems were again available in the menu on the panel. 

Yesterday evening, I deleted the menuitem with alacarte, and since then, I am not able to make it reappear, neither in the menu, neither in alacarte. 

Does alacarte not always show all available entries, even if they are set to not show up in the menu on the panel? Or does it remember that I deleted it and therefore not show it anymore? 

Francesco

---

### Post by frafu on 2007-08-19
I think that I have found what is going on. 

Alacartes does indeed remember what the user did with it; it does so in: 
/home/username/.local/...
(I don't remember the complete path, but it should be easy to find it with a search for the keyword alacart.)

---

