---
title: "How to update apt-get software indexes offline"
date: 2008-06-26
forum: General Help
---

### Post by cadcrazy on 2008-06-26
As we know we have to update software indexes (by apt-get update) before we begin installing software during fresh install. Is there any way to update the software indexes on the machine having no internet connection. Now plz plz don't suggest me the nonetdebs way, it is for downloading packages and dependencies. I want to just update software indexes.

In which files these indexes are stored when i apt-get update so that i can copy that file to the machine with no internet connection.

Any help ?

---

### Post by iaculallad on 2008-06-26
> **cadcrazy said:**
> 
In which files these indexes are stored when i apt-get update so that i can copy that file to the machine with no internet connection.

Any help ?

Try to browse this directory for the Ubuntu Software Indexes:

> /var/lib/apt/lists

---

### Post by cadcrazy on 2008-06-26
Thanks for your reply buddy. Actully I have internet connection but my friend don't have it. So can i safely replace all files from this directory to one in my friend's without damaging breaking anything.

All this i need is so that i update indexes in his computer, copy all the packages from my /var/cache/apt/archive to his and do apt-get to install any software/package. I guess now i can do that

---

### Post by iaculallad on 2008-06-26
> **cadcrazy said:**
> Thanks for your reply buddy. Actully I have internet connection but my friend don't have it. So can i safely replace all files from this directory to one in my friend's without damaging breaking anything.

All this i need is so that i update indexes in his computer, copy all the packages from my /var/cache/apt/archive to his and do apt-get to install any software/package. I guess now i can do that

Assuming that you both installed the same Ubuntu version, then, I think that would be safe.

---

### Post by cadcrazy on 2008-06-26
Thanks iaculallad. 
Will try it

---

### Post by zj3t3mju on 2008-06-28
you can try this [http://ubuntuforums.org/showthread.php?p=5283298]("http://ubuntuforums.org/showthread.php?p=5283298")

---

