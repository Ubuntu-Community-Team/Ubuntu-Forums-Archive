---
title: "basic question - folder icons location?"
date: 2018-09-29
forum: General Help
---

### Post by babag on 2018-09-29
'm experimenting with openbox/idesk/lubuntu 18.04 and am running into a basic issue. in trying to put icons on my desktop i can't find where the icons for things like home, desktop, documents, download, etc are stored. i've been looking all through /usr/share and can't seem to find them. where do i find these icons? i just want to associate an icon with a short script but can't find them.

thanks,
babag

---

### Post by ajgreeny on 2018-09-29
There are usually many in **/usr/share/icons** subdirectories but perhaps they mostly depend on a desktop environment being installed.

If you wish you can install something like **wm-icon**s package which will put all its icon files in **/usr/share/icons/wm-icon**s and you can then choose from those.

There are lots of *icon* packages available in the repos and you can find them all with command **dpkg -l *icon*** so make your choice.

---

### Post by babag on 2018-09-29
thanks, ajgreeny. 

i'd just as soon not install more stuff. i'll look into this idea, though. i really just want to find the ones that are there already. found some in a gnome subfolder of /usr/share/icons but they were orange, not the blue ones in my default setup.

thanks again,
babag

---

