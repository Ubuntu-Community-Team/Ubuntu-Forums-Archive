---
title: "Set Default Window Manager?"
date: 2007-01-21
forum: General Help
---

### Post by rj686 on 2007-01-21
I have the xsession set to XGL, but by default it loads metacity and not beryl. Is there anyway to change it so it doesn't boot to XGL by default?

Also I've noticed that right when i installed beryl window resizing was fast and so was opening programs but not it takes a while, and resizing is an eye-sore. Is there a specific version that doesn't seem to have these issues? (I know it's buggy because it's new software, i just thought I'd ask)

---

### Post by Amackera on 2007-01-21
Beryl runs in tandem wit XGL, does it not? You need to run beryl-manager in order to start Beryl. Just set it to autostart when you begin a new session.

---

### Post by rj686 on 2007-01-21
> **Amackera said:**
> Beryl runs in tandem wit XGL, does it not? You need to run beryl-manager in order to start Beryl. Just set it to autostart when you begin a new session.

I don't understand why it doesn't boot beryl by default, because beryl-manager is loaded in startup programs.

---

### Post by Pathfinder_ on 2007-02-04
i have the same problem. i have beryl manager loaded on start up but it loads metacity instead of beryl and its really anoying becasue i have to select beryl everytime. btw im running AIGLX not XGL. does anyone have a solution to this?

---

### Post by bencarrington on 2007-08-30
I'm using compiz fusion.  To get it to load compiz instead of metacity I went to Menu>System>Preferences>Sessions.  I added a new entry called "Compiz" with the command 
> compiz --replace

To do this for Beryl just call the entry "Beryl" and use the command
> beryl-manager

I used Beryl for a while and this worked.  Adds a couple of seconds to log in though.

---

