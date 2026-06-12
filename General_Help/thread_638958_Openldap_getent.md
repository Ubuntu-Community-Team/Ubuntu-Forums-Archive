---
title: "Openldap getent"
date: 2007-12-12
forum: General Help
---

### Post by jericho99 on 2007-12-12
when i do a getent passwd ive got a result like this

admin : x : 500:500:admin:/home/admin:/sbin/nologin
dave : x : 540:546 : dave :/home/david:/bin/bash

but when i do getent group i get 

postdrop : x : 108:
kingl : x : 111:
site1 : x : 499:
this is where the small probleme begin
admin:*:500:
service_ftp:*:200:david
service_imap:*:201:david

you see i ve got star instead of a x

so my problem is that i use a c function 

getgrgid who doesn work because of the *

so is there a way to get a result with a x

---

