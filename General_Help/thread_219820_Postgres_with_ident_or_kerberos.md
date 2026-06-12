---
title: "Postgres with ident or kerberos"
date: 2006-07-20
forum: General Help
---

### Post by fatalwall on 2006-07-20
Hi, I'm trying to set up a server with Postgres8.1. I have managed to figure out how to configure kerberos for the login on the computer but i cant seem to get Postgres8.1 to work right. 

I tried using ident thinking the server will pass it off to the domain controler to confirm it though i dont think thats working
host    all         root        192.168.168.0/32      ident sameuser

I can log onto the database with accounts made using the console but not remotely or over the nic. I have changes the listening port to '*' and restarted ther service several times.

I was thinking I would try just using Postgres' kerberos functionality but theres hardly anything i can find out there on the topic. Ive been stuck on this for about 2 weeks now with out any luck or progress. HELP PLEASE!!

---

