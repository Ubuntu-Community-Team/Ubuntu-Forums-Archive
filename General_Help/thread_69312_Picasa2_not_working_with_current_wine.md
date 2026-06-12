---
title: "Picasa2 not working with current wine"
date: 2005-09-26
forum: General Help
---

### Post by salsafyren on 2005-09-26
Hi, 

I have installed the latest wine with the following line in sources.list:

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

Also, I have installed picasa2.

When I run 'wine Picasa2.exe' I get the following error:

$ wine Picasa2.exe
Warning: Language 'en_DK' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_DK' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_DK' was not recognized, defaulting to 'en_US'.
Xlib:  extension "GLX" missing on display ":0.0".
fixme:ole:CoResumeClassObjects stub
fixme:urlmon:CoInternetGetSession (0, 0x7b8cd4ac, 0): stub
err:ole:CoGetClassObject class {79eac9e2-baf9-11ce-8c82-00aa004ba90b} not registered
err:ole:create_server class {79eac9e2-baf9-11ce-8c82-00aa004ba90b} not registered
wine: Unhandled exception (thread 0009), starting debugger...
Warning: Language 'en_DK' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_DK' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_DK' was not recognized, defaulting to 'en_US'.
Usage: winedbg [--command cmd|--auto] [--gdb [--no-start] [--with-xterm]] cmdline

Does anybody have picasa working?

/Chris

---

### Post by greenstar on 2005-09-27
Why not use something open source or at least written for linux?

Have you tried gthumb or Eye of Gnome as viewers/organizers?  Gimp for editing? There are probably others.

greenstar

---

### Post by salsafyren on 2005-10-27
[QUOTE=greenstar]Why not use something open source or at least written for linux?

Have you tried gthumb or Eye of Gnome as viewers/organizers?  Gimp for editing? There are probably others.

greenstar[/QUOTE]

Have you tried picasa2? It is very slick, it has cool effects and is more mature than f-spot.

Now it works with wine 0.9!

/Chris

---

### Post by MemoryDump on 2005-11-18
[QUOTE=salsafyren]Have you tried picasa2? It is very slick, it has cool effects and is more mature than f-spot.

Now it works with wine 0.9!

/Chris[/QUOTE]
has anyone been able to print using wine/picasa2 yet?
thxs
-MD

---

