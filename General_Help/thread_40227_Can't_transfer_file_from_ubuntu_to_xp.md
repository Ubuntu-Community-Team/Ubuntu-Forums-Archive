---
title: "Can't transfer file from ubuntu to xp"
date: 2005-06-08
forum: General Help
---

### Post by ihot on 2005-06-08
Dear all,

Help me please... i need to transfer some file to XP but there's problem.... "access denied". but when I took some file from XP to ubuntu there was no problem, i already check samba, its installed. 
I tried make doc share on ubuntu, and when i open from explorer XP i can't get in, need user and password, but when i fill with user and password, its denied. Need help please. Thanks.

Regards,
newbie   :smile:

---

### Post by daveisadork on 2005-06-08
[QUOTE=ihot]Dear all,

Help me please... i need to transfer some file to XP but there's problem.... "access denied". but when I took some file from XP to ubuntu there was no problem, i already check samba, its installed. 
I tried make doc share on ubuntu, and when i open from explorer XP i can't get in, need user and password, but when i fill with user and password, its denied. Need help please. Thanks.

Regards,
newbie   :smile:[/QUOTE]

Sounds to me like the easiest thing would be to edit /etc/samba/smb.conf and make the following changes or additions:

```
security = share
```  
```
null passwords = yes
``` 
This is going to be much less secure, since it will allow anyone access to the stuff that you have shared, but that sounds like what you're after. Good luck!

---

### Post by ihot on 2005-06-09
thank you very much... it's work  :grin:

---

