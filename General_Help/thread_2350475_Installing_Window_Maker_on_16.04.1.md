---
title: "Installing Window Maker on 16.04.1"
date: 2017-01-24
forum: General Help
---

### Post by tpelle2 on 2017-01-24
I downloaded and installed Ubuntu 16.04.1 - the plain Desktop version with Unity - and I'd like to try Window Maker.

I downloaded it, but following their published instructions, when I did the ./configure, I got the following error:

checking for X... no
configure: error: The path for the X11 files not found!
Make sure you have X and it's headers and libraries (the -devel packages
in Linux) installed.

Any tips on how to fix this?  (Please be gentle....I'm a newbie.)

---

### Post by tpelle2 on 2017-01-30
OK, This was easy.  After doing some more digging around on the web, I found a How-To that gave me this Bash shell command:

sudo apt-get install wmaker

Worked like a charm.  Now the fun starts to get all of the menus configured for my system.

---

