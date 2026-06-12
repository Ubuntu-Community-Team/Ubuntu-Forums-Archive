---
title: "Gentoo -&gt; Kubuntu"
date: 2005-06-28
forum: General Help
---

### Post by jago25_98 on 2005-06-28
Following LugRadio live I'm thinking of moving from Gentoo to Kubuntu:

- to save time
- to try something different
- to act as a stable base to run unstable masked Gentoo packages from

I'm worried some of the rarer applications I use won't be in Universe:

[indent]
- kmess 
- k3b
- lives (video)
- avidemux2
- totem
- rezound
- jbidwatcher
- konverter
- tor
- gtop
- kdirstat
- krename
[/indent]

---

### Post by Knome_fan on 2005-06-28
Hi, I think most, if not all of the apps you mention are available.

However, don't take my word for it, but take a look here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Have fun!

---

### Post by jago25_98 on 2005-06-28
Thanks for that link. I checked them out. These packages weren't found:

- kmess x
- lives (video) x
- avidemux2 x
- jbidwatcher x
- konverter x 
- gtop x 

So as a result I've decided to dual boot Gentoo and Ubuntu. I'll chroot into Gentoo and have a menu or xterm run things. 

Unfortunately they'll have to be 2 processes for the menus; one for Gentoo and one for Ubuntu. I'm trying to find a way round that, like writing to a file in /tmp from Ubuntu, that records the command to run in Gentoo.

Lots of work to do.

---

### Post by Knome_fan on 2005-06-28
Hi, I took a look around and it seems that you can get at least some packages, although they are not in the official repositories.

Kmess:
[http://kmess.sourceforge.net/download/](http://kmess.sourceforge.net/download/)
There you'll find a package for kubuntu

lives:
[http://www.xs4all.nl/~salsaman/lives/downloads.html](http://www.xs4all.nl/~salsaman/lives/downloads.html)
You'll find a debian package there that also works on ubuntu

jbidwatcher:
According to the homepage, all you have to do is download the .jar file and start it (You of course have to have java installed before, take a look at [www.ubuntuguide.org](www.ubuntuguide.org) on how to do it)

Konverter:
The debian package from konverter works on hoary
[http://www.kraus.tk/projects/konverter/packages/konverter_0.93-1_i386.deb](http://www.kraus.tk/projects/konverter/packages/konverter_0.93-1_i386.deb)

I don't have a clue what gtop is (althoug there is libgtop in hoary, but I don't think that's what you mean) and you probably won't get around to compiling avidemux yourself.

---

### Post by jago25_98 on 2005-06-28
wow, thanks, really quick setup on those - so easy with dpkg --install

---

