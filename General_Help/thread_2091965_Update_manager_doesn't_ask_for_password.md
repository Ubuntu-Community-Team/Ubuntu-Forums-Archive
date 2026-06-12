---
title: "Update manager doesn't ask for password"
date: 2012-12-06
forum: General Help
---

### Post by bilkay on 2012-12-06
Since upgrading to 12.04, the update manager usually doesn't ask for a password, although sometimes it does.

How is this possible?

---

### Post by grahammechanical on 2012-12-06
> How is this possible?

Because 12.04 is designed to work that way. The developers have made a serious attempt to reduce the number of times that the user has to authenticate an action. 

It is known that when users are frequently asked for a password they sometimes put in the password without investigating who or what is asking for it. So, the system becomes less secure. Malicious code might be run with the users permission because the user was in the habit of quickly typing in their password.

By reducing the need to enter a password to those times when it is necessary for security reasons, it is hoped that we users will be working safer.

Do we really need to enter a password to authenticate an update? I do not think so.

Regards.

---

