---
title: "&quot;Show splash screen on login&quot; missing from 'Session Options'"
date: 2007-05-30
forum: General Help
---

### Post by wie6Ein0 on 2007-05-30
I'm wanting to disable the Gnome splash but found that it's not showing in my 'Session Options' window.

From what I've researched, there should be three options: *Show splash screen on login*, *Ask on logout*, and *Automatically save changes to session*.

On my setup, the only option displayed is *Automatically save changes to session*.

I'm not sure what to do now... Is there a tweak that will make these options available like they should be?

---

### Post by coldstatue on 2007-06-05
same problem here. I only have the one option. I cannot add a new session either. When I save a session, it doesn't remember what programs were running. I was hoping to have Sunbird load on desktop 1, FF on 2, Thunderbird on 3... etc. Not sure if those can be session managed or not, but I want to start with getting the options that help lists as being there.

---

### Post by NilsE on 2007-06-05
I wonder where they went.  It was definitely there at some point.

A couple of the options are in Gconf (Configuration Editor) under apps/gnome-sessions.  The splash screen option is separate in system preferences also.

---

### Post by colo505 on 2007-06-10
sudo apt-get install gnome-splashscreen-manager

System > Preferences > Splash Screen

Uncheck show splashscreen

---

