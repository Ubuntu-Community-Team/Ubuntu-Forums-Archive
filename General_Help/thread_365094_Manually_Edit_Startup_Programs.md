---
title: "Manually Edit Startup Programs"
date: 2007-02-19
forum: General Help
---

### Post by CocoAUS on 2007-02-19
So I added "beagled" to the startup (using the Sessions manager) without checking to see if it was already there first.  Now there are two "beagled" entries, the Sessions manager won't give me an option to delete either one, and neither of them show in my .config/startup folder.  How can I remove the second "beagled" entry?

---

### Post by kerry_s on 2007-02-19
Use the process manager to kill it. I hate that auto save session feature,  i would just turn it off and> killall beagle < then put beagle in the startup. That session saver is just a pain the neck disable it and just use session startup to start what ever you want, take control back.

---

### Post by CocoAUS on 2007-02-19
Worked wonders.  In fact, just the killall command removed it from the startup.  :)  Thanks.

---

### Post by Bossieman on 2007-02-21
I dont get it. what exactly am I supposed to do to remove one of hthe 2 entrieses og beagled in the startup manager?

---

### Post by CocoAUS on 2007-02-23
Just try a killall beagled and see if that does it.

---

