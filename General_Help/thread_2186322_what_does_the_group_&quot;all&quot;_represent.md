---
title: "what does the group &quot;all&quot; represent?"
date: 2013-11-06
forum: General Help
---

### Post by phu004 on 2013-11-06
When&#12288;I  use the "groups" command to find out what group a user belongs to, I get "all". Can anyone tell me what does the group "all" represent?

Thanks in advance

---

### Post by drmrgd on 2013-11-06
I don't think that 'all' is a standard system group.  Perhaps the sysadmin created a group called all at some point?  If you look in /etc/password or /etc/group, do you see a group there called 'all'?

---

### Post by deadflowr on 2013-11-06
> **drmrgd said:**
> I don't think that 'all' is a standard system group.  Perhaps the sysadmin created a group called all at some point?  If you look in /etc/password or /etc/group, do you see a group there called 'all'?

I would agree with this.

How many users have admin rights?

Adding, by users I mean people users.

---

### Post by tgalati4 on 2013-11-07
I've never seen it.  So unless someone created it, I don't believe it is a standard linux group or a placeholder for "all" groups.

---

### Post by phu004 on 2013-11-07
Thanks for the reply. The user is on Ldap, when I log on as him and simply run "groups" on the terminal I get:     

"aLL groups: cannot find name for group ID 1098557572"

I have configured my ubuntu to accept users from a remote ldap server.   On the server I noticed that the user does belong to a group called "all",  but that user also belongs to other groupsas well.
I guess there is something wrong in my ldap configurations.

---

