---
title: "Postgresql install: invalid user `postgres'"
date: 2014-11-25
forum: General Help
---

### Post by bmw-man on 2014-11-25
I was trying to rename the default user for Postgresql from postgres to postgresql (long story). Now it won't start at all. I even uninstalled/reinstalled. Is there a way to force the postgresql service to run under postgresql, instead of postgres? Thanks! 


[COLOR=#29F914][FONT=Andale Mono][COLOR=#c33720]root@kali[/COLOR]:[COLOR=#5330e1]/[/COLOR]# service postgresql start[/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono]install: invalid user `postgres'[/FONT][/COLOR]



[COLOR=#29F914][FONT=Andale Mono]postgresql:x:118:127:PostgreSQL administrator,,,:/var/lib/postgresql:/bin/bash [/FONT][/COLOR]

---

### Post by bmw-man on 2014-11-25
I figured it out myself :)

Need to edit /usr/share/postgresql-common/init.d-functions file and change this line install -d -m 2775 -o postgres -g postgres /var/run/postgresql

---

