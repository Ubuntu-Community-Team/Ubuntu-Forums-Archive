---
title: "amarok with gnome"
date: 2007-03-04
forum: General Help
---

### Post by hardyn on 2007-03-04
im sure this has been asked before, but i cant find it.

installed amarok, am trying to run under gnome, but getting PILES of errors, a assume i am missing some KDE dependencies, what do i need to make it work correctly?

thanks.

---

### Post by kodoku on 2007-03-04
how did you install it?

try enabling all your repositories, then:

sudo aptitude update

then,

sudo apt-get --purge remove amarok

then,

sudo aptitude install amarok

Also, it'd be useful to know what kind of errors you're getting.

---

### Post by hardyn on 2007-03-04
they were allready enabled.  before i installed the first time.

---

### Post by hardyn on 2007-03-04
These are the error im getting.

---

### Post by hardyn on 2007-03-04
repaired by getting the perms /home/$user/.kde  ownership and perms. to $user and +RW

---

### Post by navneeth on 2007-03-04
Use this guide, it worked for me. 
[http://www.debianadmin.com/install-amarok-144-music-player-in-ubuntu-edgy.html](http://www.debianadmin.com/install-amarok-144-music-player-in-ubuntu-edgy.html)

To get the current version, change 1.4.4 to 1.4.5.

---

