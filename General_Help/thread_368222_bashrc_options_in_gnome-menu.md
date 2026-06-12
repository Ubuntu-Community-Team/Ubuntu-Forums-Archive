---
title: "bashrc options in gnome-menu"
date: 2007-02-23
forum: General Help
---

### Post by phoqueyoo on 2007-02-23
I made some aliases and have some options that I use for some applications that are stored in my bashrc file but when I launch them from the gnome-menu they are ignored. I tried 'application in terminal' and that doesn't work either. Does anyone know how I can make the gnome-panel use my bashrc file?

---

### Post by gradedcheese on 2007-02-23
I wonder if you can do this? (I have no idea personally).  Lets say the launcher was "firefox", try:

```

. ~.bashrc; firefox

```

So basically "source .bashrc and then launch firefox"

---

### Post by phoqueyoo on 2007-02-23
. ~/.bashrc; firefox works when i launch it from the terminal but it didn't work when I added it to the panel. Neither did sh ~/.bashrc; firefox. Any other suggestions?

---

### Post by kobyl on 2007-11-14
best workaround I know is setting your environment variables in ~/.gnomerc.

hope this helps

---

