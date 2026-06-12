---
title: "copying user and groups from one install to the next"
date: 2007-03-06
forum: General Help
---

### Post by sumadartson on 2007-03-06
I've recently setup a new feisty install on a recently acquired box. I'd like to copy my user and group definitions from an old edgy install however; passwords, group memberships, etc.

What would be the best way to go about migrating this? I've so far understood that I'll need to copy /etc/passwd, but that's about it.

cheers,

Suma

---

### Post by kidders on 2007-03-06
Hi there,

How many users are we talking about?

If the number is small, a safer approach would be to construct a list of "useradd" and "groupadd" commands, based on the accounts you want to copy.

---

### Post by sumadartson on 2007-03-06
Not that many, but with some fairly unique settings for group permissions. I guess I could do it by hand, but I was curious whether this could be done quickly and automatically.

---

### Post by kidders on 2007-03-06
> **sumadartson said:**
> Not that many, but with some fairly unique settings for group permissions.Permissions settings are filesystem-dependent, so you won't need to worry about copying those.

> **sumadartson said:**
> I guess I could do it by hand, but I was curious whether this could be done quickly and automatically.If you were certain that you really did want to duplicate _all_ users & groups, you *could* simply copy all the authentication-related files from /etc. This is rarely the case though. If you compare all the accounts with UIDs and GIDs under 1000 on both Ubuntus, you may find that they don't match up properly. If you understand what you're doing, that would be okay though.

If, on the other hand, you're not terribly familiar with shadow-based authentication management in Linux, you should probably be a bit more careful. For instance, something **awk -v LIMIT=1000 -F: '($3>=LIMIT) && ($3!=65534)' /etc/passwd** would show you the portion of /etc/passwd it would definitely be safe to copy between two Ubuntu systems. You could do something similar with other files (such as /etc/shadow).

---

