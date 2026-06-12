---
title: "Compositing issue"
date: 2013-02-08
forum: General Help
---

### Post by mikerocks18 on 2013-02-08
new to linux but not nearly to pcs. i have Lubuntu 12.10 but was wanting a more streamlined app dock then what i  got it with so upon looking online i found Docky to be suggested. the problem is when its launched it states that i need to configure my settings or else it will not work to the fullest or at all. i finally found how to enable composting but it still wont allow me to use any of Dockys setting to mainly auto hide so it doesn't eat a quarter of my screen. really want this to work since i much prefer linux to XP

---

### Post by PowerBarry43 on 2013-02-08
Hi

My preferred dock is actually cairo-dock which I would recommend for easier customisation but if you're set on docky you need to get a compositing window manager such as metacity which is part of gnome or compiz,

to install compiz open a terminal and run:

```
sudo apt-get install compizconfig-settings-manager
```

There is tons of material out there, but a google search away on how to set up compiz with docky on ubuntu but here is a sampling of the results I get from googleing "docky compositing"

[http://askubuntu.com/questions/31379/docky-enable-compositing-error-and-black-bar-visualized-instead-of-it](http://askubuntu.com/questions/31379/docky-enable-compositing-error-and-black-bar-visualized-instead-of-it)

[http://ubuntuforums.org/showthread.php?t=1601887&page=3](http://ubuntuforums.org/showthread.php?t=1601887&page=3)

Hope this helps!

Barry

---

### Post by mikerocks18 on 2013-02-08
honestly which ever is actually better. i had gotten metacity and the other supposed programs to run this setup but to no gain. but if your sugested program is better ill give it a whirl.

---

### Post by claracc on 2013-02-09
You have to enable compositing in metacity in order docky works properly.

To do it, you will find this link: [https://help.ubuntu.com/community/Metacity](https://help.ubuntu.com/community/Metacity) useful, in particular point B.- Configuration editor.

I have docky in my ubuntu 12.04 gnome fallback desktop system with metacity and it uses to work well except sometimes on booting system, docky looses weather and trash applets and I have to add them again.

---

