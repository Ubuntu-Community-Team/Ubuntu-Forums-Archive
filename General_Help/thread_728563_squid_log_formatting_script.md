---
title: "squid log formatting script"
date: 2008-03-18
forum: General Help
---

### Post by tr3s on 2008-03-18
hi!

this topic is more on scripting issue

i have a file "smutwords" that contains all the words i want to filter from the squid logs so that when i issue the command ```
cat /usr/local/squid/var/logs/access.log.0 | grep -f /home/admin/smutwords > smutlist
``` i can get all the sites (games, porn, etc) that has been accessed by the clients in my network that should be blocked by squidguard but aren't.

the problem is the output file (smutlist) is not so human readable and contains multiple entries of the sites. so i was wondering how can i display only the domain of the site and only 1 entry of that domain to make the list short.

what other commands do i need to add to the command above?

tnx in advance

---

