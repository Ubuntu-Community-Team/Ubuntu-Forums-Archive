---
title: "SSH login lubuntu"
date: 2019-01-07
forum: General Help
---

### Post by legtdl2 on 2019-01-07
Hello!
Just installed lubuntu on my raspberry pi b+.
Cant find how to login via ssh.
Password?
Please help.
Kindest regards
Michael in Sweden

---

### Post by TheFu on 2019-01-07
Did you install the **openssh-server** package?
While you are at it, probably want **fail2ban** too - so brute force attacks get blocked ASAP.
And is the firewall active and 22/tcp open?

---

