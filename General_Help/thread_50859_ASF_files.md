---
title: "ASF files"
date: 2005-07-21
forum: General Help
---

### Post by Ferio on 2005-07-21
Is there any way to see .asf files in Ubuntu? I¡ve got one of these, but it says it can't play it. Maybe I need some codec?

---

### Post by GTvulse on 2005-07-21
Hola Ferio,

you need to enable the extra repositories in Synaptic (Universe and Multiverse) as well as add the Backports repositories. Edit the repositories listing in Synaptic and when prompted add these lines as custom repositories:

```
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

Reload the package catalogs, ignore the warning due to a lacking gpg signature, and search in Synaptic for Mplayer, and w32codecs. I've tried with other video players available in the repositories, including VLC, and the only one that has worked for me when trying to view anything encoded with Windows Media codecs has been Mplayer.

Notice that there is a backports mirror in Spain, so you may want to use that one. Check the correct addresses at [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

---

### Post by Ferio on 2005-07-22
Oh, man, I had all these yet, but I was trying to open the file via double click and it didn't work! Summer is slowing my brain, definitely. Thank you very much!

---

### Post by jatos on 2005-07-22
[QUOTE=Ferio]Oh, man, I had all these yet, but I was trying to open the file via double click and it didn't work! Summer is slowing my brain, definitely. Thank you very much![/QUOTE]
 I use kaffeine to play ASF's, is there any way of porting that to gnome?

---

### Post by bored2k on 2005-07-22
[QUOTE=jatos]I use kaffeine to play ASF's, is there any way of porting that to gnome?[/QUOTE]
 You could still use it on Gnome, it would take 3 generations to open in comparison to gnome native, but It would work. AFAIK, kaffeine uses the xine engine? If so, Gxine/Xine-ui would perform the same, although yes, I love kaffeine. If it wasn't KDE native..

---

