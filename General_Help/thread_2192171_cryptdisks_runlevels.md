---
title: "cryptdisks runlevels"
date: 2013-12-06
forum: General Help
---

### Post by helloworld1215 on 2013-12-06
It is specified that the cryptdisks run levels are 0 and 6, but in various tutorials it does not specify to make any changes to these run levels despite specifying configuration in /etc/crypttab. 

1. Does /etc/crypttab in fact getting initialized on a default Ubuntu installation? (12.04+)
2. If so, how does it do so if cryptdisks does not appear to be started on the 2 runlevel?
3. If it is initialized by cryptdisks, how does cryptdisks do so at boot if it is not on the 2 runlevel?

I don't want to break my boot so I would like to fully understand how crypttab works before making any changes which is the reason I am asking this instead of experimenting.

---

