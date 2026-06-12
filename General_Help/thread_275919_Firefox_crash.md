---
title: "Firefox crash"
date: 2006-10-12
forum: General Help
---

### Post by LaurentR2 on 2006-10-12
Hello,

I'm using Edgy and since a moment Firefox crashes with a "segmentation fault" message. I don't know if it's a bug I should report or a problem I can repair. I've made my upgrade from dapper to edgy and my version of firefox now is 1.99+2.0rc2+dfsg-0ubuntu1

Thank you,

---

### Post by epennings on 2006-10-12
Does it crash immediately after you start Firefox or while browsing?
It might have something to do with plugins that aren't installed correctly.

---

### Post by LaurentR2 on 2006-10-12
It crashes immediatly after I start firefox. But it's special to Kubuntu Firefox, since I've downloaded Firefox from Mozilla website and launched it from his repertory and it works.

---

### Post by ansi on 2006-10-12
> **LaurentR2 said:**
> It crashes immediatly after I start firefox. But it's special to Kubuntu Firefox, since I've downloaded Firefox from Mozilla website and launched it from his repertory and it works.


Remove all installed plugins && extensions, and try again. Try to start FF from another user in your system too.

---

### Post by LaurentR2 on 2006-10-12
After removing all extensions it works again. Thank you...

---

### Post by Deathmoon on 2006-10-29
I'm having the same problem on Edgy...

How do you uninstall flash; it seems to be the plug-in that crashes?  Also, is there another flash install that works for FF?

**********************************

I placed:
export XLIB_SKIP_ARGB_VISUALS=1

At the beginning of the file:  sudo gedit /usr/bin/firefox

all is working now...not sure what this flag does but it's no longer crashing.

**********************************
Update...
Ok, I installed Edubuntu Edgy onto another machine and it works perfect.  Hmm...

---

