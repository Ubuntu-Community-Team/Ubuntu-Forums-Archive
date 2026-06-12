---
title: "Error &quot;groups: cannot find the name for the group with ID .....&quot; Realm + SSSD"
date: 2019-02-13
forum: General Help
---

### Post by marcelo.tissoni on 2019-02-13
Dear, good afternoon.


I have added a computer with Ubuntu 18.04.2 LTS to my Active Directory, through SSSD and Realm, the operation is correct, I can log in with several users perfectly.


But I have the following problem, when I open a terminal after logging-in with a domain user, I get the following error in the terminal:


"groups: can not find the name for the group with ID [COLOR=#242729][FONT=Arial]1399400513[/FONT][/COLOR]"


This doesn't happen with local users.


Thank you


[ATTACH=CONFIG]282501[/ATTACH]

---

### Post by SeijiSensei on 2019-02-14
You need to examine /etc/group.

ID 13 is usually assigned to the "proxy" group.

```

$ more /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:syslog,phl
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
[etc.]

```

Does the domain user have a corresponding entry in /etc/passwd?  (I've not used MS domain integration.) If so, what group is that user assigned to? 

```
seiji:x:1000:1000:SeijiSensei,,,:/home/seiji:/bin/bash
```

That entry shows I have user ID 1000 and group ID 1000.  What does the corresponding item in /etc/passwd say for domain users?

If the domain users have /etc/passwd entries, then I'd create a separate group for domain users and assign them all to that.  See "man adduser" for details.

---

### Post by marcelo.tissoni on 2019-02-14
Thanks for replying!

The ID is not 13, is 1399400513, sorry!

It seems to me that the ID refers to some group of the active directory domain, because all the users I login with have the same ID in the terminal.

---

### Post by SeijiSensei on 2019-02-16
The maximum for user and group IDs in *nix is 65535.  So yes, that group is coming from AD.

I can't help any more since I know nothing about integrating with AD.

---

