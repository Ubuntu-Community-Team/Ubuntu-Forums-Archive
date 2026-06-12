---
title: "User not found in User Manager"
date: 2018-08-04
forum: General Help
---

### Post by andyhelloween on 2018-08-04
Good day all,

I'm running Kubuntu 16.04.05. When log in with my user (User A), if I go to User Manager, I can see all users of the system as expected.
However, if I logged with my wife's user (User B), and go to User Manager, the only user I cannot see in User Manager is mine (User A).

Both users are defined as Administrators.

Do you have any idea what I can check? I have no trouble using the system with any user... but still, would like to understand what is going on, especially before upgrade to 18.04.

Kind regards,
Andres.

---

### Post by TheFu on 2018-08-05
Check the group memberships using 'id' - what is different?
Also, I don't think User Manager honors LDAP users.

---

### Post by andyhelloween on 2018-08-14
Hi TheFu, thanks for your response.

I did check 'id' and there is nothing different.

---

### Post by TheFu on 2018-08-14
> **andyhelloween said:**
> Hi TheFu, thanks for your response.

I did check 'id' and there is nothing different.

How do I say this nicely ... prove it.  Please.

---

### Post by andyhelloween on 2018-08-16
> **TheFu said:**
> How do I say this nicely ... prove it.  Please.

Touché!

id user1 with my user "user1":

```
[FONT=monospace][COLOR=#000000]uid=1001(user1) gid=1001(user1) groups=1001([/COLOR][/FONT][COLOR=#000000][FONT=monospace]user1[/FONT][/COLOR][FONT=monospace][COLOR=#000000]),4(adm),27(sudo),113(lpadmin),127(sambashare),130(davfs2)[/COLOR],1002(generalgroup)[/FONT]
```[COLOR=#000000][FONT=monospace]
[/FONT][/COLOR]
id user1 w[FONT=monospace]ith my wife's user:

[/FONT]```
[FONT=monospace][COLOR=#000000]uid=1001(user1) gid=1001([/COLOR][/FONT][COLOR=#000000][FONT=monospace]user1[/FONT][/COLOR][FONT=monospace][COLOR=#000000]) groups=1001([/COLOR][/FONT][COLOR=#000000][FONT=monospace]user1[/FONT][/COLOR][FONT=monospace][COLOR=#000000]),4(adm),27(sudo),113(lpadmin),127(sambashare),130(davfs2)[/COLOR],1002(generalgroup)[/FONT]
```[FONT=monospace]

[/FONT][FONT=monospace]


[/FONT]

---

### Post by TheFu on 2018-08-16
I  expected two different userids since the complaint is that two different userids aren't both acting like admins.  You pasted user1 ... and only user1.  Where's the other user?

---

### Post by andyhelloween on 2018-09-13
[COLOR=#000000]Oops... sorry!

id **user1** with my user "user1":

[/COLOR]```
[COLOR=#000000][FONT=monospace]uid=1001(user1) gid=1001(user1) groups=1001([/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=&amp][FONT=monospace]user1[/FONT][/FONT][/COLOR][/COLOR][COLOR=#000000][FONT=monospace][COLOR=#000000]),4(adm),27(sudo),113(lpadmin),127(sambashare),130(davfs2)[/COLOR],1002(generalgroup)[/FONT][/COLOR]
```[COLOR=#000000][FONT=monospace]

[/FONT][/COLOR][COLOR=#000000]id **user2** w[/COLOR][COLOR=#000000][FONT=monospace]ith my wife's user:

[/FONT][/COLOR]```
uid=1000(user2) gid=1000(user2) groups=1000(user2),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),113(lpadmin),127(sambashare),1002(generalgroup)
```


I ended up going for the upgrade to 18.04.1 and everything is working fine. Do you find anything unusual in those ids?

Thanks much for your time!

---

