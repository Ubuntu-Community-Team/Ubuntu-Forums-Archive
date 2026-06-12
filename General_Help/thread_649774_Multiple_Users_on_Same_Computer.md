---
title: "Multiple Users on Same Computer"
date: 2007-12-25
forum: General Help
---

### Post by mistypotato on 2007-12-25
Hello, after searching for about 45 minutes and not getting the specific information need, I decided it is time to seek help.

I have several family users who all use the same Linux computer.  So, I set up accounts (logins?) for each family member.

Problem is....I can't seem to remove things from the non-Admininstrative users (everyone except me) menus.

For example under Applications I do not want System Tools to show up.

However, I have been through everything I can think of and can't fugure out out to remove things from other users menus that I don't want there such as configuration and system tools type things.

Thanks for you help in advance.

---

### Post by taurus on 2007-12-25
As long as they don't belong to groups adm & admin in /etc/group, they can't use/run those apps anyway.  So basically, they can't use sudo/gksudo.

---

