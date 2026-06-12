---
title: "apt-get update errors"
date: 2005-05-17
forum: General Help
---

### Post by xodeus on 2005-05-17
Hi. I've some major errors in my apt-get
Tried to google them but with no solutions that worked.
A solutions that could work was to edit /etc/apt/apt.conf
with adding
APT::Cache-Limit 10000000; 
That was something I fund on some debian maillists.
But it didnøt work.
So.
I've started a small thread about it here [http://www.ubuntuforums.org/showthread.php?t=35018](http://www.ubuntuforums.org/showthread.php?t=35018)
as I though it would be the best place to put it, but with no replies.
So please help.

---

### Post by harryc on 2005-05-17
This is what I'd do. Backup your current etc/apt/sources.list. Put in a new sources.list that looks likes this one (#4) 

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Do a sudo apt-get update

If that still fails, your database may be corrupt. You'd need to rebuild it, but I do not know the command to do that in a debian environment. Perhaps try a sudo apt-get clean

---

