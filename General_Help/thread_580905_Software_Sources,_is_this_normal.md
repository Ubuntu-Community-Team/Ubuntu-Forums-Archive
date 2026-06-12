---
title: "Software Sources, is this normal?"
date: 2007-10-19
forum: General Help
---

### Post by Lavender Dream on 2007-10-19
Can anyone quickly check that when you go to **System** -----> **Software Sources**, under the **Ubuntu Software** tab, you see TWO listings of the same "Cdrom with Ubuntu 7.10 Gutsy Gibbon" with the bottom one checked under 'Installable from CD-ROM/DVD'? Is this normal? Can someone explain what this is about?

I'm under a fresh, clean installation of 7.10 from alternate i386 CD.

My pastebin of source.list: [http://paste.ubuntu-nl.org/41171/](http://paste.ubuntu-nl.org/41171/)

Also under Third-Party Software tab, I see two listings of _[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner_ and _[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner (Source Code)_
Can you explain what this is too?

Trying to learn here and see why it's showing a duplicate from my first question. Thank you very much in advance. :KS

---

### Post by davidjmayo on 2007-10-19
> Can anyone quickly check that when you go to System -----> Software Sources, under the Ubuntu Software tab, you see TWO listings of the same "Cdrom with Ubuntu 7.10 Gutsy Gibbon" with the bottom one checked under 'Installable from CD-ROM/DVD'? Is this normal? Can someone explain what this is about?


Yes it's normal to see CD-ROM checked
When you want to install extra packages (which you can do in a variety of ways ie use synaptic or add/remove programs or apt-get or aptitude) you are asked to insert the CD. If the package is there it will load from the CD not the internet --  this  version will install but obviously is not the latest (if there have been updates for security or a bug patch for instance) so then you need an internet connection but it will still run

Really you don't need the CD option so if you have a good net connection so you can just click to unselect it. After that you won't be prompted to insert the install CD and the package you want will be the latest from the repositories.

---

### Post by Lavender Dream on 2007-10-20
Thank you very much for the prompt response davidjmayo. I was just curious why there were two of the same listed there and only one of it checked. :KS

---

