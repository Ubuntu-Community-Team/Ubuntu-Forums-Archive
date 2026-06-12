---
title: "Evolution Calendar notices"
date: 2024-05-16
forum: General Help
---

### Post by bookscrounger on 2024-05-16
I am running 22.04.4 LTS.  I keep getting out-of-date Evolution calendar updates. 

Which is funny because neither Evolution emall nor calendar are set up on my machine, and when I search for it in software, I only get the option to install it.  

When I click on the updates, I cannot update, I do not go to the app.

I don't know how Evolution got on my machine, how it got into my calendar info, but I would like it to stop updating me.  I have spent some time looking around, can't find any solutions.  Thanks.

---

### Post by psychohermit on 2024-05-16
Wow, ghost in the machine.  That's strange, good luck tracking it down.

--glenn

---

### Post by paulparker2 on 2024-06-23
Self regulaly using evolution, whether closed out or running, also keep getting Evolution gnome seemingly to refresh my logins. 

 Do not know what triggers this. 

Suspicion it may be an attempt by Yahoo to refresh my login... 



My Package: 
 Ubuntu 22.04.4 LTS
evolution  Version: 3.44.4-0ubuntu2



,

.

---

### Post by #&amp;thj^% on 2024-06-23
```
cd /usr/share/dbus-1/services && ls | grep evolution
org.gnome.evolution.dataserver.AddressBook10.service
org.gnome.evolution.dataserver.Calendar8.service
org.gnome.evolution.dataserver.Sources5.service
org.gnome.evolution.dataserver.UserPrompter0.service

```
Is the trigger, but i warn about any changes to that directory. (Don't mess with it)

Please one of you file a bug-report against evolution.

---

