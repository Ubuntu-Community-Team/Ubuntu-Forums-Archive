---
title: "[SOLVED] For new user account -- how to disable / bypass password strength checking?"
date: 2007-09-15
forum: General Help
---

### Post by Phrawm48 on 2007-09-15
Feisty (7.04), Gnome.

I've tried using "System > Administration > Users and Groups", adduser, and useradd to create a new user account on my single-user desktop computer.

NONE of these tools permit me to create an alpha-only password of less than six characters.  I want to do this.

Can someone please tell me (without any lectures on security, please) how to disable or bypass this password-strength-checking behavior? 

Cheers & thanks,
Ric
SFO

---

### Post by Phrawm48 on 2007-09-16
Aha -- I figured out one way to answer my own question.[LIST=1]
[*]Use *sudo -i* to become *root*.
[*]Run *adduser*.  New user accounts created by root do not enforce new-password strength requirements.
[*]Click **System** > **Administration** > **User and Groups**, then configure the newly created account's group settings, etc.[/LIST]Ta da!

Cheers & hope this helps,
Ric
SFO

---

