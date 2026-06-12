---
title: "Postfix 2.2 Experimental"
date: 2005-09-08
forum: General Help
---

### Post by megamartianca on 2005-09-08
I've had nothing but grief trying to move from Ubuntu's version of Postfix (version 2.1.something) to the test version.  I've downloaded the Debian packages but get complaints about dependencies, and when I forced the install, packages like anacron were declared to be dependency faulty.  Is there any way to get to the experimental version of Postfix on Ubuntu?

---

### Post by DJ_Max on 2005-09-08
You're asking for trouble when using packages made for another distribution. Only way I see is compiling it manually or ask for a backport.

---

### Post by megamartianca on 2005-09-09
[QUOTE=DJ_Max]You're asking for trouble when using packages made for another distribution. Only way I see is compiling it manually or ask for a backport.[/QUOTE]

Well, I don't have a problem compiling manually, but anacron at least requires an MTA, and is the packaging system going to recognize a compiled variant of Postfix?  Looks like I've discovered a new upgrade hell here, and the reason to moving to Ubuntu was to escape that, so I'm getting pretty disappointed.  Surely someone must be running the experimental versions of Postfix on an Ubuntu box.

---

