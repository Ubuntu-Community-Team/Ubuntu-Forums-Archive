---
title: "[SOLVED] Remove authorization"
date: 2007-07-17
forum: General Help
---

### Post by sancho panza on 2007-07-17
When I run any graphical config program that requires authorization or use *gksudo*, the authorization stays on for a while (supposedly 15 mins). Is there an option by which I can turn off the authorization without waiting for 15 mins? Like the way its in Fedora...the bunch of keys that pop up on your panel to notify that the user is still in the authorized mode...

---

### Post by 5-HT on 2007-07-18
Hi, you can edit your /etc/sudoers to change the timestamp_timout variable
It's best to edit your sudoers file using```
sudo visudo
```[quote=sudoers manual] timestamp_timeout
    Number of minutes that can elapse before sudo will ask for
    a passwd again.  The default is 5.  Set this to 0 to always
    prompt for a password.  If set to a value less than 0 the
    user's timestamp will never expire.  This can be used to
    allow users to create or delete their own timestamps via
    sudo -v and sudo -k respectively.
[/quote]
cheers,

---

### Post by sancho panza on 2007-07-18
I'll try that...thanks!

---

