---
title: "login not poosible because no password prompt"
date: 2013-02-10
forum: General Help
---

### Post by MichaelW64 on 2013-02-10
I'm using Ubuntu 10.04 and yesterday I installed and configured LDAP  for centralized login. I created a new user "test" in the ldap directory. I wanted to login  with that user to see if it works but I could not. There was no password  prompt. What is even worse is that there is no password prompt for me  as a user local to that machine (not defined in ldap). So I'm locked out of that box. What can I do to be able to log in again?  Regards,
  Michael

---

### Post by MichaelW64 on 2013-02-10
I have teh same problem on the server. I have webmin installed on this so I could have a look at auth.log.

Trying to ssh to the server I see this entries:

```
Accepted password for michael from 192.168.1.14 port 5883 ssh2 
error: PAM: pam_open_session(): Cannot make/remove an entry for the specified session 
Received disconnect from 192.168.1.14: 11: disconnected by user 
```I did not disconnect, this happens automatically after a few seconds

---

### Post by MichaelW64 on 2013-02-10
I solved it on my laptop, here is how:

- Start from a LiveCD
- chroot to my system
- removed libpam-ldap
- removed nscd

After that I was able to login to my laptop the normal way. Don't know yet where I go from here.

The problem on the server still exists. Since this is a headless box I have no idea how to do that.

Any ideas are welcome.

---

