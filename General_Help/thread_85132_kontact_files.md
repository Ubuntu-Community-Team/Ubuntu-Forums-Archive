---
title: "kontact files"
date: 2005-11-01
forum: General Help
---

### Post by wazoo on 2005-11-01
I tried to sync my palm to Kontact, and through a series of stupid mistakes, wound up with duplicate to-do and datebook entries. The Palm is fine, so I'd like to start over. But where, exactly, are the Kontact files stored? I'd like to delete them.

---

### Post by Manny C on 2005-11-01
Kontact is a Kmail (Emails) + Korganiser (Calendar and To-Dos) + KAddressBook (Contacts) +...

So the files will be in separate folders under ~/.kde/share/apps.
[LIST=1]
[*] Kmail: ~/.kde/share/apps/kmail   
[*]Korganiser: ~/.kde/share/apps/korganizer   
[*]KAddressBook: ~/.kde/share/apps/kabc [/LIST]

---

### Post by wazoo on 2005-11-02
[QUOTE=Manny C]Kontact is a Kmail (Emails) + Korganiser (Calendar and To-Dos) + KAddressBook (Contacts) +...

So the files will be in separate folders under ~/.kde/share/apps.
[LIST=1]
[*] Kmail: ~/.kde/share/apps/kmail   
[*]Korganiser: ~/.kde/share/apps/korganizer   
[*]KAddressBook: ~/.kde/share/apps/kabc [/LIST][/QUOTE]

Thank you! Deleting ~/.kde/share/apps/korganizer/std.ics* took care of it. Now, on to NEW mistakes!

---

