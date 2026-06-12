---
title: "Pidgin - permanently remove buddy"
date: 2007-10-04
forum: General Help
---

### Post by mlanza on 2007-10-04
How do I permanently remove a buddy from my buddy list?  I remove them and when I restart pidgin, the removed buddies are back.  Shouldn't this be quite an easy task?

Thanks for any help.

---

### Post by n3tfury on 2007-10-04
i just tried this using version 2.2.0 and had no problem  :/

---

### Post by mlanza on 2007-10-04
Is your primary IM through Yahoo?  I think my buddies are being gleaned from my Yahoo address book. :)  When I was running GAIM this wasn't an issue.

---

### Post by n3tfury on 2007-10-04
no, msn, sorry.

---

### Post by slack on 2008-02-07
I get the same problem trying to remove a Y! buddy with 2.2.1.  The buddy list is actually stored in ~/.purple/blist.xml and it's pretty obvious what's going on in there if you have a poke around, so as a kludge you can open it up (when pidgin isn't running) and remove the relevant lines.  It'd be a good idea to keep a backup, though, obviously...

---

