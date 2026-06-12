---
title: "mythweb on edgy"
date: 2006-11-21
forum: General Help
---

### Post by daveyiv on 2006-11-21
Is there a good guide on making the mythweb that is distributed in the ubuntu repositories accessible from outside the lan?

maybe someone here can help, I have everything installed and mythweb is accessible from my LAN, however not from the internet. I have port 80 forwarded in my router. One interesting thing to note is that when I do a: 

netstat -anp | grep "httpd"

It doesn't return anything, so it doesn't appear that apache is even listening or something. Can anyone help me figure out what is going on?

---

### Post by adamkane on 2006-11-21
Your router may not like external IPs that attempt to acces your LAN. You may need to add a rule to allow some external IPs.

---

