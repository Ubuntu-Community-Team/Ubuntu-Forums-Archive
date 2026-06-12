---
title: "Sudo and Winbind"
date: 2008-06-20
forum: General Help
---

### Post by Causer1984 on 2008-06-20
I'm having a spot of bother trying to get my ubuntu desktop to allow sudoing for NT login groups. Basically, in my company, we have a group called BUILTIN\administrators in the Active Directory. I can log in to the linux box with my NT username using winbind and everything's fine. What I now want to do is add the administrators group to the sudo list so any of my colleagues can sudo to their hearts' content.

If I add my NT name explicitly to the sudoers file it works. However, even though my sudoers file shows the BUILTIN\administrators group is in the list of allowed sudoers, when I try to sudo it says I am not on the sudo list. I have tried removing the BUILTIN\ to no avail.

**Content from /etc/sudoers**
```

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%BUILTIN\administrators ALL=(ALL) ALL

```

**(snipped) Output from groups:**
```
user@computer$ groups
domain users domain admins administrators BUILTIN\administrators BUILTIN\users
```



Just for prosperity here's the contents of my **/etc/pam.d/sudo**
```
auth sufficient pam_winbind.so
auth sufficient pam_unix.so use_first_pass
auth required   pam_deny.so

@include common-auth
@include common-account

```

Any help gratefully accepted. Apologies if I haven't made myself clear enough. I'm more than happy to expand if required.

---

### Post by Causer1984 on 2008-06-20
As a followon (and because it's important) here's the relevant section for **/etc/nsswitch.conf**
```

passwd:         compat winbind
group:          winbind compat
shadow:         compat
hosts:          files dns mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis



```

---

### Post by Causer1984 on 2008-06-24
Right, I think I've got to the bottom of it. Basically, two things:

[LIST=1]
[*]Sudo doesn't like backslashes (\)
[*]Sudo doesn't like spaces
[/LIST]

I was getting confused because I saw I was in a group administrators and tried it and it didn't work. In fact, it was part of a bigger group like "antivirus administrators". I snipped the "groups" output because I thought the extra groups were irrelevant. Guess that's the last time I decide what's important and what's not on this forum.

Anyway, hope this will help someone else.

---

### Post by la11111 on 2012-03-05
In case you don't know what OP is talking about with spaces and backslashes, you just need to be sure to escape them because they are special characters. i.e., don't do this:

DOMAIN\username ALL=NOPASSWD: ALL

do this:

DOMAIN**\\**username ALL=NOPASSWD: ALL

It took me a second to figure out what OP was saying so I thought I'd pitch in a couple cents ;)

---

### Post by oldos2er on 2012-03-05
Closed, necromancy.

---

