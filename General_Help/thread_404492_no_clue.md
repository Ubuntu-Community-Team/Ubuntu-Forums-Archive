---
title: "no clue"
date: 2007-04-08
forum: General Help
---

### Post by tachyon462 on 2007-04-08
after auto-upgrading a couple apps ubuntu kinda went loopy.
right after logging in I hear the startup sound see a black screen for half a second and before the sound is done playing I'm back at the login screen....what the s***?
if anyone out there has any ideas that could avoid me a complete reinstall I would be happy to hear them.

---

### Post by bashologist on 2007-04-08
Maybe try starting gnome from a terminal? I think the command is "startx" or something. If something goes wrong with this command you should then see an error message. There's also probably an error message somewhere in /var

Were you trying to install or upgrade beryl maybe? I have had a similar problem when trying to install beryl once.

---

### Post by tachyon462 on 2007-04-08
beryl was indeed on the list.  I'll try from the terminal.
this just had to happen when I was getting all excited and ready to get rid of windowsall together.....looks like I might hang on to it for a while longer.

---

### Post by bashologist on 2007-04-08
> **tachyon462 said:**
> beryl was indeed on the list.  I'll try from the terminal.
this just had to happen when I was getting all excited and ready to get rid of windowsall together.....looks like I might hang on to it for a while longer.

The problem might already have been fixed. It could be as simple as logging into a terminal with ctrl+alt+f2 then sudo apt-get update && sudo apt-get dist-upgrade

Personally I wouldn't automatically execute beryl on startup.

---

### Post by tachyon462 on 2007-04-08
no good......still the same problem.
is there a way to remove beryl from the startup script from the terminal?
my command line knowledge isn't exactly the greatest (but I"m learning)

---

