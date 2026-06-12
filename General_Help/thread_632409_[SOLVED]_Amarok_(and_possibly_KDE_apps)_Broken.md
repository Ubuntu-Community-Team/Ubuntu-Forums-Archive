---
title: "[SOLVED] Amarok (and possibly KDE apps) Broken"
date: 2007-12-05
forum: General Help
---

### Post by Rabidmonkey1 on 2007-12-05
Hi everyone, interesting problem I have here - it seems the KDE apps I have installed in Gutsy are having a hard time starting/functioning correctly... 

Primarily, I use Katapult and Amarok.  Katapult seems to be working now (though there is no tray icon), but Amarok refuses to start.

I get this in the terminal:
```
bob@bob-desktop:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?
```

Tried a reinstall and sudo apt-get -f install with no luck...  Any ideas how I can get it working again (short of switching to KDE?)

Thanks!

---

### Post by FuturePilot on 2007-12-05
Try
```
amarokapp
```

---

### Post by Rabidmonkey1 on 2007-12-06
Sorry, nothing with that either...  Thanks for the response.

---

### Post by Rabidmonkey1 on 2007-12-06
Hmm... not sure why but things seem to have sorted themselves out and the apps are working again...  ahh well.  Thanks everyone!

---

### Post by hangover27 on 2007-12-09
Any chance you found out what caused it to start working again?
I have the same problem with amarok. If I log in as a different user it works fine, so I figure it's something in ~/.kde, but what?

---

### Post by Rabidmonkey1 on 2007-12-09
Honestly, I have no idea.  One day it didn't work, the next it did.  I'm thinking it may have had something to do with DCOPserver failing to boot up correctly...  Check the order of your bootup processes, you know what I mean?

---

