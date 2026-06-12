---
title: "Where to put programs"
date: 2004-12-09
forum: General Help
---

### Post by lameth on 2004-12-09
I'd like to keep my system as clean and professional as possible. With that in mind I would like to know where ubuntu installs programs and where generally it creates symlinks.
I know all this is taken care of by apt but not all the programs I may download are going to come in deb packages. In those cases I don't want to put them just "anywhere" I'd like to put them with the other programs on my system and create any symlinks in /usr/share, for instance.

---

### Post by hashimoto on 2004-12-10
[QUOTE=lameth]I'd like to keep my system as clean and professional as possible. With that in mind I would like to know where ubuntu installs programs and where generally it creates symlinks.
I know all this is taken care of by apt but not all the programs I may download are going to come in deb packages. In those cases I don't want to put them just "anywhere" I'd like to put them with the other programs on my system and create any symlinks in /usr/share, for instance.[/QUOTE]
 I guess the recommended place is either /usr or /opt. 

See [http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

BR
Hashimoto

---

### Post by Juergen on 2004-12-10
[QUOTE=hashimoto]See [http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)[/QUOTE]
And looking there you will find:
"These days, '/usr/local' is widely regarded as a good place in which to keep self-compiled or third-party programs."

---

### Post by wulf on 2004-12-10
[QUOTE=Juergen]And looking there you will find:
"These days, '/usr/local' is widely regarded as a good place in which to keep self-compiled or third-party programs."[/QUOTE]
 I've recently installed Ubuntu and, like lameth, I was also wondering about keeping things tidy. The particular avenue I was pondering was what would be involved in setting up a local repository, creating my own .deb files for applications I can't find even in the multiverse, and thus allowing me to manage all the software on the machine with synaptic (brilliant program!) or CLI equivalents?

Is there a guide somewhere on creating your own personal repository?

Wulf

---

### Post by p!=f on 2004-12-10
[QUOTE=wulf]I've recently installed Ubuntu and, like lameth, I was also wondering about keeping things tidy. The particular avenue I was pondering was what would be involved in setting up a local repository, creating my own .deb files for applications I can't find even in the multiverse, and thus allowing me to manage all the software on the machine with synaptic (brilliant program!) or CLI equivalents?

Is there a guide somewhere on creating your own personal repository?

Wulf[/QUOTE]
[http://www.debian.org/doc/manuals/repository-howto/repository-howto.html](http://www.debian.org/doc/manuals/repository-howto/repository-howto.html)

---

### Post by wulf on 2004-12-10
[QUOTE=p!=f][http://www.debian.org/doc/manuals/repository-howto/repository-howto.html](http://www.debian.org/doc/manuals/repository-howto/repository-howto.html)[/QUOTE]
 Lovely - thanks for that :D

Wulf

---

### Post by El Cubano on 2005-01-27
You may also want to check out this detailed HOWTO that I have written on how to create an automatic .deb repository.

[http://familiasanchez.net/~sanchezr/?page=debrepository](http://familiasanchez.net/~sanchezr/?page=debrepository)

---

### Post by fng on 2005-01-28
[QUOTE=El Cubano]You may also want to check out this detailed HOWTO that I have written on how to create an automatic .deb repository.

[http://familiasanchez.net/~sanchezr/?page=debrepository](http://familiasanchez.net/~sanchezr/?page=debrepository)[/QUOTE]

That guide looks great.
Gonna try it whenever my first package comes out.

Any chance for a noobish package howto?

---

### Post by El Cubano on 2005-01-28
[QUOTE=fng]That guide looks great.
Gonna try it whenever my first package comes out.

Any chance for a noobish package howto?[/QUOTE]

I am certainly open to the idea.  What topics did you have in mind?

---

