---
title: "gedit: export highlighted code to html"
date: 2008-06-25
forum: General Help
---

### Post by johnconnor on 2008-06-25
Hi everyone!

I'd like to know how to export a syntax-highlighted code in gedit as a HTML file, to include this highlighted code in a web page. I found the HTML export plugin for gedit on [this page]("http://live.gnome.org/Gedit/Plugins"), but I don't know how to install it...

Can anyone help me?

---

### Post by 505 on 2008-06-25
Download the file from Bugzilla, as mentioned on the page. Open the file with the archive manager and have a look at the INSTALL file, it will describe how to install it.

---

### Post by johnconnor on 2008-06-25
Thank you for taking the time to reply to my question but if I'm asking this, it's because I already tried what you suggest. Did you try to install it? I'm running Gutsy and here's what I did:
[LIST]
[*]./configure
[INDENT]It worked apparently[/INDENT]
[*]make
[INDENT]I get this: *make: *** Pas de cibles spécifiées et aucun makefile n'a été trouvé. Arrêt.* (sorry it's in french, it says no target no makefile)[/INDENT]
[*]make check
[INDENT]I get this: *make: *** Pas de règle pour fabriquer la cible « check ». Arrêt.* (no rule to build target "check")[/INDENT]
[*]make install
[INDENT]I get this: *make: *** Pas de règle pour fabriquer la cible « install ». Arrêt.* (no rule to build target "install")[/INDENT]
[*]make install-sh
[INDENT]I get this: *make: Rien à faire pour « install-sh ».* (nothing to do with "install-sh")[/INDENT]
[/LIST]
What else can I do to make it work?

---

### Post by johnconnor on 2008-06-26
No idea?

---

### Post by Mr. Picklesworth on 2009-12-19
Found this thread on Google. Uh, for what it's worth (I know this thread is really old), the plugin uses autogen, so you need to run the autogen.sh script first (./autogen.sh), then make :)

First, run # apt-get build-dep gedit-plugins

---

