---
title: "Peer authentication failed connecting to postgres db"
date: 2014-02-17
forum: General Help
---

### Post by mike146 on 2014-02-17
[COLOR=#000000][FONT=Arial]Hi 

I'm getting the following and the other solutions I've seen for this don't seem to be working... 
Within the ubuntu server terminal (a virtualbox vm) I am running a python script that can be found on the tutorial link below (I changed the user and db names to match what I had set up locally): 
Error FATAL: Peer authentication failed for user "a4apps"
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]My Ubuntu server os user name is the same. 

I have restarted my postgres a few times. 

I have tried changing my pg_hba.conf file by: 
changing the IPv4 host method from md5 to "trust" 
and by adding a line under it: 
"host.......... all........... all.............. myubuntuserverip/32........... trust"
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I am trying to access the database via a python script. 

I am using psycopg to make that possible.[/FONT][/COLOR]
con = psycopg2.connect(database=[COLOR=#800000]'fieldtest2'[/COLOR], user=[COLOR=#800000]'a4apps'[/COLOR])
[COLOR=#000000][FONT=Arial]
I created the user: 
sudo -u postgres create user a4apps 
superuser no, create databases yes, create other users no. 

Created database: sudo -u postgres createdb fieldtest2 -O a4apps
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I was following this tutorial: [here]("http://zetcode.com/db/postgresqlpythontutorial/")
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I'm running out of ideas. Any guidance would be appreciated. 
Thanks 
Mike[/FONT][/COLOR]

---

### Post by mike146 on 2014-02-18
Solved. I had to change the unix local users from peer to trust in the pg_hba.

---

