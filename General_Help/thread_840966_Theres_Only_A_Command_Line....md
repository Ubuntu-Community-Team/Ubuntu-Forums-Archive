---
title: "Theres Only A Command Line..."
date: 2008-06-25
forum: General Help
---

### Post by MMasterson on 2008-06-25
I just installed Ubuntu Server (Most Recent) about 10 minutes ago. Wile rebooting it was fine. In the asked me to login, it was all text based. Theres no GUI it was only text based, everything was text based. All I see now if a command line...

Can anyone help me fix this issue?

Please and Thank You!

---

### Post by tamoneya on 2008-06-25
the difference between server and desktop is that there is no GUI by default in server.  This is because most servers dont need to have a GUI.  If you want one however just type this in command line.```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by x1a4 on 2008-06-25
> **MMasterson said:**
> Can anyone help me fix this issue?

There's nothing to fix.  This is a feature.  On the vast, vast majority of servers a GUI is a complete waste of resources.  Still, if you insist on having a GUI you can install one from the myriad of graphical interfaces in the repositories.

---

### Post by MMasterson on 2008-06-25
OK, I did what you requested now it says

*Reloading System Log Daemon...

Just wait?

---

### Post by John.Klockenkemper on 2008-06-25
> **x1a4 said:**
> There's nothing to fix.  This is a feature. 

I love to hear those words.

---

### Post by x1a4 on 2008-06-25
Hit enter, if you get the prompt, you're done.

---

### Post by MMasterson on 2008-06-25
Wow! Thanks A Lot!

To all the others, I'm sorry I'm new to Linux, I don't know everything.

---

### Post by mikjp on 2008-06-26
Server edition is meant for servers, not for desktops. You can build your own custom lightweight system for example for an old computer on top of the server install, but you should in that case have at least some idea about what you are doing. 

greetings,

m

---

