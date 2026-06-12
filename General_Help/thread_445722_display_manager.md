---
title: "display manager"
date: 2007-05-16
forum: General Help
---

### Post by b9anders on 2007-05-16
I had Entrance set up as my display manager, but after a reboot, it didn't load properly and X doesn't start, and couldn't Enlightenment to start because of it either from the command line (don't know the command for initiating a gnome session). Prior to the boot, I had in a gnome session

disabled gdm from running on startup since entrance was my default display manager

and

used this command from get-e.org to try and change the login theme for entrance:
```
entrance_edit --theme <path to theme file>
```

I have a feeling that it was the latter that screwed things up. I can see entrance does load on startup, but no graphic environment starts up. If I run X after logging in from the command line, it just show the grained black/white screen.

I've tried to remove entrance and reconfigure gdm as my standard display manager and re-install entrance and reconfigure that as my default display manager, but none of it worked.

I am a bit fecked. Anyone who can offer some help as to how to resolve this?

***Edit: Just tried running 'startx' now and it logs me into GNOME, so I got that working. Just not getting a graphic login option. ***

---

### Post by b9anders on 2007-05-16
^ 

 :-/

---

### Post by b9anders on 2007-05-16
:(

---

