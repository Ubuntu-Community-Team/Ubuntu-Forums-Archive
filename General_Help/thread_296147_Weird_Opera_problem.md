---
title: "Weird Opera problem"
date: 2006-11-09
forum: General Help
---

### Post by Lasse_ on 2006-11-09
Hi guys!

I'm having some really strange problem with Opera 9.02. I booted my laptop to Ubuntu Dapper and tried to start Opera from the programs menu - nothing happened. After that I switched to terminal to get some info about the browser crashing on start up. These two lines came up: 

ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.

I have tried to boot the computer and re-install the application several times with no luck, browser won't start. The strange thing here is that in System monitor I can see the app running but operapluginwrapper is a zombie. Actually there are two of those pluginwrappers as zombies.

Any thoughts?

 - Lasse

---

### Post by jazzgossen on 2006-11-09
This has to do with the Java plugin (JVM = Java Virtual Machine). So there is probably a problem with your Java installation. Check the Opera Linux forum, I think I remember that you can try starting opera with the command line option --debugjava, or something similar.

---

