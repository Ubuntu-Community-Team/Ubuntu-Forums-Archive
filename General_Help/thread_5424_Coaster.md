---
title: "Coaster"
date: 2004-11-18
forum: General Help
---

### Post by TravisNewman on 2004-11-18
This looks like a promising burner, but I can't seem to get it ./configure'd

There are some dependencies I know I haven't installed yet (waiting to get the problematic ones out of the way)... here's what I get:
```

configure: error: Library requirements (shared-mime-info >= 0.14 gthread-2.0 >= 2.4.0 libxml++-2.6 >= 2.6.1 bakery-2.4 >= 2.3.8 libgnomeui-2.0 >= 2.0.0 libnautilus-burn >= 2.8.5) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```

And the README states:
```

Coaster requires the following libraries and their dependencies:
libxml++-2.6.1 (ftp://ftp.gnome.org/pub/gnome/sources/libxml++/2.6/)
libgnomeuimm-2.6.0
bakery-2.3.8 (ftp://ftp.gnome.org/pub/gnome/sources/bakery/2.3/)
nautilus-cd-burner-2.8.5

```

**shared-mime-info >= 0.14** -- I have 0.15-1ubuntu1
**gthread-2.0 >=2.4.0** -- haven't bothered yet
**libxml++-2.6 >= 2.6.1** -- I have 2.6.1-2
**bakery-2.4 >= 2.3.8** -- haven't bothered yet
**libgnomeui-2.0 >= 2.0.0** -- I have 2.8.0-0ubuntu1
**libnautilus-burn >= 2.8.5** -- I have nautilus-cd-burner 2.8.5, as it mentions in the README file, but not this specific package.

According to the readme, it SEEMS that bakery should be all I need... I have libgnomeuimm-2.6.0 installed as well, though it didn't exactly give me any output about that when trying to ./configure, the libgnomeui-2.0 error may be somewhat related. Anyone have any ideas here?

---

### Post by TravisNewman on 2004-11-18
OK I think it just reports back with the error when one or more of the dependencies are missing... I installed bakery, and it got past all that, but...

*** Ooops, couldn't find xmlcatalog.  Actually this should
*** never happen at this point, which means your system is really broken.

uuuhhh.... anyone?

---

### Post by TravisNewman on 2004-11-18
Fixed, had to reinstall xmlcore. Dunno why, but it configured :)

---

### Post by TravisNewman on 2004-11-18
OK its installed. On the website, it says that it can create audio cds, but I'm not seeing ANYTHING to suggest that it can. I wanted to get away from k3b because it needs KDE stuff that I want to get rid of. Anybody have any experience with Coaster and know how to make an audio cd?

---

### Post by ulrich on 2004-11-18
hi,
i know my answer isnt related to coaster, but i hope its usefull.

i just discovered 'mr.burns' (for audio-cds only) that someone nice wrote. this guy has also an ubuntu repository for some of his apps (and so mr.burns) and for me it works like a charme.
the gui is even simpler than coaster :)

[http://www.grawert.net/software/](http://www.grawert.net/software/)

---

### Post by jdong on 2004-11-18
[QUOTE=panickedthumb]OK its installed. On the website, it says that it can create audio cds, but I'm not seeing ANYTHING to suggest that it can. I wanted to get away from k3b because it needs KDE stuff that I want to get rid of. Anybody have any experience with Coaster and know how to make an audio cd?[/QUOTE]

Remind me what's wrong with having KDE libs installed, unless you're REALLY short on disk space?

---

### Post by TravisNewman on 2004-11-18
Yeah Mr. Burns always crashes when I hit "burn"

And I just mean I want to get away from using KDE stuff in Gnome, because it takes longer to load. I don't mind having KDE libs installed, it's just the load time. And K3B just isn't working properly for me yet (some mp3 files that it says it can't understand, etc, when they seem to be encoded exactly the same).

---

### Post by bdoetsch on 2004-11-28
Hmm...tried to build it myself, but can't get it to go past the xmlcatalog issue. Reinstalling xml-core didn't help either. Anyone has any idea how to proceed?

Best regards, Bastian

---

### Post by taygan on 2004-12-07
xmlcatalog is installed with the xml2-utils package.

---

### Post by jdong on 2004-12-07
[QUOTE=panickedthumb]Yeah Mr. Burns always crashes when I hit "burn"

And I just mean I want to get away from using KDE stuff in Gnome, because it takes longer to load. I don't mind having KDE libs installed, it's just the load time. And K3B just isn't working properly for me yet (some mp3 files that it says it can't understand, etc, when they seem to be encoded exactly the same).[/QUOTE]


Hmm, the KDE app load time is approximately equal to any gnome app's load time... Ubuntu doesn't do the whole kdeinit+kbuildsyscocoa thing.,

---

