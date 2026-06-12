---
title: "[SOLVED] Unused users and groups"
date: 2008-02-12
forum: General Help
---

### Post by csb1227 on 2008-02-12
So, there are many, many users and groups already present on my install.   Users such as...daemon, bin, sys, sunc, games...  Groups of the same names, of course but also groups like dial out, fax, voice, cdrom...

Can I safely get rid of all these users and groups I'm not using?

Thanks

---

### Post by apetresc on 2008-02-12
> **csb1227 said:**
> So, there are many, many users and groups already present on my install.   Users such as...daemon, bin, sys, sunc, games...  Groups of the same names, of course but also groups like dial out, fax, voice, cdrom...

Can I safely get rid of all these users and groups I'm not using?

Thanks

NO!

You may not be using them, but they're users used by the system for various applications. Different processes take on different UID's to manage permissions and things like that. Removing them may (is very likely to) break those applications.

Other groups exist to manage permissions. For example, if you ever create a new user, they will only have access to /usr/games if you add them to the games group. These groups are there for a reason!

Leave them there, they're not hurting anybody :D

---

### Post by csb1227 on 2008-02-12
What about all those users in Samba?

---

### Post by apetresc on 2008-02-12
> **csb1227 said:**
> What about all those users in Samba?

Those are users that SAMBA uses for authentication. If you no longer use those (because you've removed the share or whatever), you should use Samba's tools for removing these users, not remove them directly yourself. There's some info on that [here](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch10_:_Windows,_Linux,_and_Samba).

But seriously, this isn't like Windows where users are things you're supposed to log in as. They have a much more abstract meaning in UNIX-based systems, and it's perfectly normal for a system to have dozens of users that a human never touches explicitly. This is fine.

Those users do not cost you any performance or diskspace, but removing the wrong one may cause many unexplainable problems down the road. I highly reccomend you leave them there unless you're very sure about what you're doing.

---

### Post by csb1227 on 2008-02-12
Thanks!

---

