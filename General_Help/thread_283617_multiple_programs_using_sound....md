---
title: "multiple programs using sound..."
date: 2006-10-24
forum: General Help
---

### Post by Choad on 2006-10-24
i have had this before when using a fluxbox based ubuntu install, and now on my new xubuntu install i am getting the same thing.

i am setting myself up with xubuntu because i dont need the wifi any more (that was the only thing keeping me with windows really...)

if i use more than one sound program, the sound fails on all except the first program started. i believe this is quite a common problem but i havent been able to fix it. something to do with sound servers i believe?

also, what would be the best music player for xubuntu? i had a look at rhythm box, but it wanted to install a gnome library file, and i want to avoid doing that...

thanks

---

### Post by hw-tph on 2006-10-24
You need to set up either a sound daemon (esound is common and the standard for Enlightenment and Gnome) or ALSA software mixing using the dmix plugin. You can achieve that by simply editing your ~/.asoundrc or /etc/asound.conf according to [the documentation](http://alsa.opensrc.org/DmixPlugin).

For music I prefer using [Quod Libet](http://www.sacredchao.net/quodlibet). The website is currently in a sorry state but 0.24 was just released. Ubuntu 6.10/Dapper ships with the old 0.18 release and a lot has changed since so I suggest installing from the QL subversion repository. To make sure you have everything you need before installing 0.24 you can type **sudo apt-get build-dep quodlibet**.


Håkan

---

### Post by Choad on 2006-10-24
but why the hell would i have to do this? surely this should be one of those incredably basic things that a distro like ubuntu should have sorted out of the box?

---

