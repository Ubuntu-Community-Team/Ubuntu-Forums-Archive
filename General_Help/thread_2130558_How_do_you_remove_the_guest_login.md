---
title: "How do you remove the guest login"
date: 2013-03-29
forum: General Help
---

### Post by GeorgeLSpencer on 2013-03-29
I am probably a bit of a security freak; but I consider the guest login (without a password) to be a security flaw in Ubuntu 12.02 LTS. On a normal UNIX system I would remove the entry from /etc/passwd and /etc/security/passwd, but there are no such entries on Ubuntu, so how does one block this account?

---

### Post by mcduck on 2013-03-29
It's not the same as having an actual "guest" user, Ubuntu's guest login creates a new user with extremely limited permissions every time the guest login is used, and destroyes the account again afterwards. The guest account has even less permissions than most basic normal user would have, and the home directory only exists in /tmp.

...Actually if you are concerned about security, it's probably as secure a way to let anybody else use your computer as you can get. And defintiely shouldn't be mixed with the normal guest *account* one ight have on a Unix system.

Still, if you really never need to let anybody touch your computer, and find even this level of security not enough, then edit */etc/lightdm/lightdm.conf* and add "allow-guest=false".

---

### Post by GeorgeLSpencer on 2013-03-29
Many thanks McDuck.

I would never have thought of looking in lightdm, but this should be a help, considerably. I wasn't happy with leaving a system where anyone can read files on any of the three operating systems that I have installed. Not that the Windows systems are overly secure, anyway.

Thanks again!

---

### Post by mcduck on 2013-03-30
Well, the guest login shouldn't let users do that anyway. Like I said, it's highly restricted in permissions, with no read access outside of the temporary home directory, and even accessing other drives on the system would require password confirmation. At least on 12.10, but I'm quite sure it was the same way on 12.04 as well..

---

