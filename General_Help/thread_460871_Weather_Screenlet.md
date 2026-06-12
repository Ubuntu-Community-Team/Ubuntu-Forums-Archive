---
title: "Weather Screenlet?"
date: 2007-06-01
forum: General Help
---

### Post by blade22 on 2007-06-01
I have installed screenlets, and currently they all work except for the weather one. They all used to work before, however now they all work apart from the weather one. I click on add and nothing happens... Does anyone know what's wrong. Thanks for any help!

---

### Post by DracoPsycho on 2007-06-01
Go into terminal and do ```
screenletsd add weather
``` and see the output. Post it and maybe it'll give a clue.

---

### Post by cward002 on 2007-06-01
another option that I Use is the Firefox Plug-in for weather. I can't remember it's name right now. just go to the Firefox plug-ins site and do a search for weather. I couldn't get the weather Dsklet working either.

The only downside is you have to open Firefox to see the weather. but that's not a big deal.

---

### Post by blade22 on 2007-06-01
DracoPsycho: I tried your method and i comes up with the message "Class weatherScreenlet not found" does this mean I have to reinstall it?? Because I have tried to reinstall it by downloading the file off of the screenlet website and it says that it is installed.

---

### Post by DracoPsycho on 2007-06-02
The only way I can think of, is to go to /usr/local/share/screenlets and replace weather screenlets files there. 

But first, go to /home/<user>/.config/Screenlets open screenletsd.ses file and see which of the other files in this folder contains session info about weather screenlet and delete it. You'll lose configuration, but maybe screenlet itself will work again.

---

