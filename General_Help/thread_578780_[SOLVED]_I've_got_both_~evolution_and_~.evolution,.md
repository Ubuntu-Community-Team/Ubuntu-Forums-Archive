---
title: "[SOLVED] I've got both ~/evolution and ~/.evolution, do I need both?"
date: 2007-10-17
forum: General Help
---

### Post by pinkunicorn on 2007-10-17
I have both an ~/evolution directory and a ~/.evolution directory? Do I need both?

I suspect that ~/evolution is some old leftover, since Tracker seems to regard files in there as hits. I assume it's smart enough to avoid the real Evolution cache stuff. Or is that a naïve assumption?

So: can I remove one of them, and if so, which one?

---

### Post by ruibernardo on 2007-10-17
Hi pinkunicorn,

the ~/evolution/ isn't an evolution directory, but ~/**.**evolution/ is.

For example, if you had to do a backup of your evolution data (mail, calendar, contacts, etc), you should backup this three directories from your home:

~/.evolution/
~/.gconf/apps/evolution/
~/.gnome2_private/Evolution

More info about evolution directories: [http://ubuntu.wordpress.com/2005/12/03/how-to-backup-evolution/](http://ubuntu.wordpress.com/2005/12/03/how-to-backup-evolution/).

---

