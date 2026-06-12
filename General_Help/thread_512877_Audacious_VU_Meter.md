---
title: "Audacious VU Meter"
date: 2007-07-29
forum: General Help
---

### Post by steevols on 2007-07-29
I'm trying to compile VU-meter 0.4 from source, for lack of a .deb. "./configure" won't recognize that I have audacious installed at all, so I can't get a good compile. I bypassed the dependency check, but then I got a SLEW of other problems.

Does ANYONE have a link to a deb, or have a guide for installing VU-meter on Ubuntu (Feisty)?

Thanks in advance.

---

### Post by steevols on 2007-07-30
52 views and no response?

Is it even possible to get VU on Ubuntu? Does anyone have any success stories? :(

---

### Post by pjkoczan on 2007-07-30
> **steevols said:**
> I'm trying to compile VU-meter 0.4 from source, for lack of a .deb. "./configure" won't recognize that I have audacious installed at all, so I can't get a good compile. I bypassed the dependency check, but then I got a SLEW of other problems.

Does ANYONE have a link to a deb, or have a guide for installing VU-meter on Ubuntu (Feisty)?

Thanks in advance.

Whenever you're compiling from source and it's complaining about dependencies, make sure you have the appropriate *-dev package installed. This installs the library and header files which allow dependent programs to compile properly.

In short, "sudo apt-get install audacious-dev" and the run the configure script again. Repeat for any other dependent programs.

---

### Post by steevols on 2007-07-31
Audacious runs fine, it's installed completely. It's the VU-meter that I'm trying to install. There is a REMARKABLE lack of information on the internet on that program.

---

### Post by steevols on 2007-07-31
I found (finally) a tutorial, even though it applies to XMMS. Audacious should be compatible, though.

[Compiling and Installing VU Meter]("http://www.jellykernel.org/index.php?option=com_content&task=view&id=112&Itemid=49&width_set=thinfluid&lang=en")

---

### Post by smeto on 2007-11-16
audacious vu meter plugin compiled for gutsy from sources [http://www.netswarm.net/misc/audacious-vumeter-0.8.tar.gz]("http://www.netswarm.net/misc/audacious-vumeter-0.8.tar.gz")

enjoy

---

### Post by ominousluv on 2008-01-12
> **smeto said:**
> audacious vu meter plugin compiled for gutsy from sources [http://www.netswarm.net/misc/audacious-vumeter-0.8.tar.gz]("http://www.netswarm.net/misc/audacious-vumeter-0.8.tar.gz")

enjoy

Thanks for this!

---

