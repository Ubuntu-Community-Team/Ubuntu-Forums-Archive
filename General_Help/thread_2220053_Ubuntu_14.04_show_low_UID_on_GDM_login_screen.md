---
title: "Ubuntu 14.04 show low UID on GDM login screen"
date: 2014-04-26
forum: General Help
---

### Post by BFG on 2014-04-26
I have a number of users with a UID of 400, 401, 402 etc. They must be this low as there is a clash with UIDs >1000 on one of the NAS boxes.

It's always been possible for me to edit the AccountService file /etc/login.defs ( and when using lightdm, /etc/lightdm/users.conf) to change the UID_MIN values.
This works with 12.04 and GDM.

It's not working in 14.04. The changes make no difference.  Is there some new config file in 14.04 I need to change?  Gooling has come up with nothing conclusive.

---

### Post by BFG on 2014-04-27
I also tried making a change to /etc/gdm/custom.conf

[COLOR="#0000CD"][greeter]
include = user1,user2
[/COLOR]

Making this config change works in 32bit.  It's only broken in 64bit. Must be a bug?

---

