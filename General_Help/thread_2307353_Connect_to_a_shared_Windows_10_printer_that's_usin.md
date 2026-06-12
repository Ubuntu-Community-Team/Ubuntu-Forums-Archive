---
title: "Connect to a shared Windows 10 printer that's using microsoft account credentials"
date: 2015-12-24
forum: General Help
---

### Post by a.vlachos@radiokiss.gr on 2015-12-24
Hi all, 

I am trying to connect to a windows 10 shared printer. 
The windows machine has users that are using microsoft accounts, so each user has a username@domain credentials.

After a little forum search i found that in order to connect to the windows machine's shares, i have to put in the "USER" field the username without the domain, and the domain name (without the "@") should be in the "DOMAIN" field in which i was putting the workgroup name in previews windows versions which had local accounts. 

So when adding a new printer, i am entering the machine with the shared printer using the above method (it asks for username, domain and password). I am choosing the drivers and the printer is added normally.

The problem is that when the system authenticates for the printer it only asks for username and password, not domain. If i put username@domain in the username field, its not working and asks me again in an endless loop (the same applies in all things when trying to connect to the windows machine but in the others it ask for the domain). 

I have tried various combinations for username/domain but none worked... so i can't print. 

Is there a possible solution or a way to add a default domain for that operation?

---

### Post by slickymaster on 2015-12-24
Closed. Duplicate [here]("http://ubuntuforums.org/showthread.php?t=2307352").

---

