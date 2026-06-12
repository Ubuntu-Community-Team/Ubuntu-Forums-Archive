---
title: "stupid problem"
date: 2004-11-07
forum: General Help
---

### Post by clauD on 2004-11-07
i install ubuntu base sistem for server 
a have  a user 
ex :
test
pass :test 
whem ai what to du somothing i must worck witch sudo
ex: sudo vim /etc/apt/sources.list 
BUT 
if i write su
and enter the test password is not worcking  
if ai do 
sudo adduser root >> the user exist ?!!!! 
what to do ?
ps.> sorry for my english

---

### Post by p!=f on 2004-11-07
This has been discussed several times. Answer can be found on the official website of Ubuntu Linux. Section FAQ or HOWTOs, correct me if wrong.

But to save you some time, here comes Ms. Answer.
Root password is disabled by default.

This will give you root prompt:
```

sudo -s

```

If you still want to use su,
```

su -

```
(- = login shell)

run:
```

sudo passwd root

```
to set up a password for root.

However, I don't recommend to enable it. Sudo is more powerful, not to mention root's password disabled is always an advantage.

---

