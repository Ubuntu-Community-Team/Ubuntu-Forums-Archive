---
title: "xorg.conf into multiple files?"
date: 2005-04-07
forum: General Help
---

### Post by El Rey de Todo on 2005-04-07
I'm sure this must have been brought up before, but I'll ask anyway since I couldn't find anything about it elsewhere.

Why does xorg.conf exist?  I know what it does, but why isn't it separated into like 6 files?  It seems like it would be easier to make programs to configure X if they didn't all have to worry about the entire file.

Example: fglrxconfig.  It does a decent job of generating the video section, but it destroys every other setting in the file because it just overwrites the original with a new version.  This wouldn't be a problem if input devices and modules and stuff were all in a different file.  This way you could make a GUI to change sections independently and it would actually work.

Does anyone know if it is possible to separate the config like this or if there would be any downsides?  It seems like every other config is done like this, so why not the one for X?

---

### Post by Leif on 2005-04-07
Well, maybe separating it would work, but the reasons you quote for it just sound like bad programming to me. If fglrxconfig simply asked whether or not it should touch anything that's not its business, you wouldn't have a problem.

---

