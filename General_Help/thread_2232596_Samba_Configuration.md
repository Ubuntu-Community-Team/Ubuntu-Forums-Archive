---
title: "Samba Configuration"
date: 2014-07-03
forum: General Help
---

### Post by rahul4557 on 2014-07-03
Is it possible to create shares with an admin account to control all the shared folder (read/write) and then a user share with username and password per user(ie read/write only to user with username and pass)

---

### Post by capscrew on 2014-07-03
> **rahul4557 said:**
> Is it possible to create shares with an admin account to control all the shared folder (read/write) 

Root is the only user that can modify the smb.conf file;  if that is what you mean.  If you mean can you create a share that only a specific user can access and only that user can read/write to that share; then yes you can do that also.
> 

[and] then a user share with username and password per user(ie read/write only to user with username and pass)
If you mean a usershare (a share created by a mortal user (human user)) using the GUI; then yes, but only in that users /home directory generally,   If you mean can the root user create a share for each user that is private to that user, then yes, that is what the [homes] share is all about.  You could also do this manually for each user, but that's a PITA,  With the [homes] share you set it up one time and each valid Linux/Samba user has their own private share.

---

