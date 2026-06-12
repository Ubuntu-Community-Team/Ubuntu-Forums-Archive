---
title: "postfix accepts mail from any domain"
date: 2008-01-07
forum: General Help
---

### Post by bradleyd on 2008-01-07
Hello everyone,
I have a postfix server setup to query LDAP for alias maps. When I telnet into postfix and do rcpt to: [email]anyone@anywhere.com[/email], I get OK, and it does not query LDAP. 
If I enter rcpt to: bob, then Postfix queries LDAP and rejects based on bob is not a user. 
I am trying to have Postfix only accept mail for it's domain. Lets say test.lab, and then check if user exists @ test.lab. 
Thanks for your time,
Brad

---

### Post by bradleyd on 2008-01-30
nevermind, got it working:)

---

