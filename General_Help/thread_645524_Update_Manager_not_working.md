---
title: "Update Manager not working?"
date: 2007-12-20
forum: General Help
---

### Post by SilentTim on 2007-12-20
So I noticed the other day that I haven't had any notifications from update manager for quite a while. When I open update manager and ask it to check for updates, it always says my system is up-to-date.

I can still install individual packages from synaptic and add/remove software, but they always have one stage where they go through a load of errors like the following:

```

Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
--12:03:16--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving nchc.dl.sourceforge.net... failed: Connection timed out.
--12:03:26--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
--12:03:36--  http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving umn.dl.sourceforge.net... failed: Connection timed out.
--12:03:46--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Which I have ignored up till now because I thought it was just trying to download some extra fonts (which I don't want anyway). I'm now wondering if I need to resolve this to make my update manager work again?

This is on a Gutsy system by the way.

---

