---
title: "sshd 'match' statement"
date: 2013-09-06
forum: General Help
---

### Post by piramiday on 2013-09-06
I'd like to write in my /etc/ssh/sshd_config file a complex statement, something like:
```
PasswordAuthentication yes
Match User john
   PasswordAuthentication no
Match User john Address 192.168.0.100
   PasswordAuthentication yes
```
the idea would be to accept password logins for every user, but for john implement more strict rules such as allowing password logins only from a certain IP address.


... unfortunately, this does NOT work. can you tell me why?

---

### Post by bluefrog on 2013-09-06
[http://yurisk.info/2011/04/05/two-tips-to-secure-ssh-access-from-specific-ips-to-specific-users-in-checkpoint-or-any-linux/](http://yurisk.info/2011/04/05/two-tips-to-secure-ssh-access-from-specific-ips-to-specific-users-in-checkpoint-or-any-linux/)

---

### Post by piramiday on 2013-09-06
that's interesting :), thank you... but referring to my original post, what would be the final setup, in your opinion?
I can't just write:
```
AllowUsers * john@192.168.0.100
```
can I?

---

### Post by piramiday on 2013-09-06
I think I got it!


the problem was the ORDER of the two 'match' statements.
```
PasswordAuthentication yes
Match User john Address 192.168.0.100
   PasswordAuthentication yes
Match User john
   PasswordAuthentication no
```
works as it should: login requests for user john are accepted from 192.168.0.100 and rejected from 192.168.0.66, with any other user unaffected.


\\:D/

---

### Post by Habitual on 2013-09-06
that rocks on 2 points.
**You** found your own solution and
That is a very clever way to keep users fixed to one IP for ssh

---

### Post by bluefrog on 2013-09-06
As I don't really like pasting links without trying them, I tried... and failed.
Unable to use AllowUsers and AllowGroups at the same time in an easy way.

In the end, I would use PAM to restrict users. It seems to be much simpler, at least to me.

edit /etc/pam.d/sshd and add
account required pam_access.so

edit /etc/security/access.conf and add in your case
- : john : ALL EXCEPT 192.168.1.100

you could also deny all other users by adding them to a group (ssh-no) and restrict the group. You would need in that case to add all the other users to the ssh-no group
- : ssh-no : ALL

you could use a ssh-restricted group, a ssh-ok group and so on...

---

