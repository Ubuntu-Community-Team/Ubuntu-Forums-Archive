---
title: "Join Ubuntu desktop to samba domain"
date: 2016-02-06
forum: General Help
---

### Post by alex501 on 2016-02-06
Hello everyone. 

I have searched for two days a tutorial on how to add a Ubuntu desktop client to a samba domain , and tried 3-4 tutorials with no success. 

So far i have samba configured that i can add windows clients. A few lines in smb.conf no more. I'm using 15.04 server and i already joined a windows 7 VM , so i know it works. 

If someone could point me in the right direction with a tutorial or anything , i would be really grateful.

---

### Post by gordintoronto on 2016-02-06
Samba doesn't create a domain, so you can't "join the domain." In Ubuntu's file manager, click on "Network" and keep going until the shared folder shows up.

---

### Post by alex501 on 2016-02-06
Sorry , I meant I need server authentication for a Ubuntu desktop . Like I said I already did that to a windows 7 . I read something about winbind and LDAP , but what i found was ancient . Sorry , I'm still fairly new to Ubuntu .

---

