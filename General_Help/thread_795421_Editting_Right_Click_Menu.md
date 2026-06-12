---
title: "Editting Right Click Menu"
date: 2008-05-15
forum: General Help
---

### Post by Tyrfing on 2008-05-15
Hello, my laptop is running Hardy Heron, but my work computer is running RedHat Enterprise.


One feature that I really like about Redhat Enterprise is that if you right click on the desktop, the first item on the menu is a command to open a terminal. I like the feature so much, in fact, that I continually try and do this on Ubuntu, and get sad because the menu is different.


Is there anyway to edit this right click menu? I specifically want to add an "Open Terminal" option, but if it is easy to configure, making other changes would also be nice.


Thanks!

---

### Post by loserboy on 2008-05-15
i believe it's called nautilus scripts, ill go look and find out

edit: ok this looks like what you want, designed for and older ubuntu but should work fine [http://ubuntu-tutorials.com/2006/12/29/right-click-to-launch-custom-scripts-with-nautilus-ubuntu-6061-610/](http://ubuntu-tutorials.com/2006/12/29/right-click-to-launch-custom-scripts-with-nautilus-ubuntu-6061-610/)

---

### Post by Tyrfing on 2008-05-15
Thanks, that definently worked, but I was wondering if there was a way to edit it in more detail... like having the open terminal command appear outside of a scripts folder, and removing the things from the right click menu that I don't need. What you showed me did work, and will be useful, but I am wondering if there is more I can do.

---

### Post by loserboy on 2008-05-15
i've been meaning to do the same thing, and i'm sure you can... i'm at work but i'll see what i can find

---

### Post by loserboy on 2008-05-15
well, this has more stuff [http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/) and if you just google "nautilus scripts" theres a number of pages related.... but I know what you're looking for and i can't seem to find a place that shows you how to fully customize the menu.... actually for gutsy development a while back i requested a graphical interface to be able to do that, but maybe it's just not out there... perhaps a trip over to the nautilus devs would give us more info.

---

### Post by Alex6969 on 2008-05-15
Thanks! I've been wondering how to do this for a while now.

---

### Post by mano cazalet on 2008-05-15
there's an other option called [nautilus-actions]("http://www.grumz.net/?q=")

available in synaptic. It places a menu entry in System/Preferences.

---

### Post by aroch1 on 2008-05-16
g-scripts and nautilus actions both accomplish this, but opening a terminal from the Nautilus context menu is a common enough idea that there's actually a plugin already written for it.  Try installing nautilus-open-terminal, restarting nautilus (killall nautilus) and check out your context menu.

---

