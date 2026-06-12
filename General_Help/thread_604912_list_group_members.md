---
title: "list group members"
date: 2007-11-06
forum: General Help
---

### Post by jimmywu013 on 2007-11-06
Hi,

Is there a command-line way to list all members of a group?  The users & groups admin tool in ubuntu can do this, but there must be some way to do it without the GUI.  The /etc/group file only lists groups, not members.  The id and groups commands list groups the current user is member of.  I haven't found anything that works the other way, ie lists all users in a group.  

Thanks in advance,

Jimmy

---

### Post by p_quarles on 2007-11-06
There sure is:
```
groups *username*
```

---

### Post by Fireal on 2008-02-26
That lists the groups a user is a member of.  I am also interested in finding a command that lists all the users that constitute a group. 
 i.e. "command groupname"  lists out user1 user2 user3 etc.  

I also confirmed that if I use > groups user3 it spits out ftp as the only group but if I look at /etc/group all I see is > ftp: x:1006: with no user names.

---

### Post by Fireal on 2008-02-26
Found it > sudo apt-get install members
members *groupname* 

---

