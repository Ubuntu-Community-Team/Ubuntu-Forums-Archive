---
title: "Samba Read Only Drive"
date: 2013-04-18
forum: General Help
---

### Post by jkdunne on 2013-04-18
A client of mine has an Oracle Financials Finance System. When making payments the payment file is dropped out of Oracle Financials to a Samba Drive. It is then uploaded to their banking system by logging into the banking system and locating the file. My issue is that while the bank file is located on the Samba drive before upload to the banking system that the file can be changed. This means someone could change bank accounts for payees etc.

Is there any possible way to prevent anyone from modifying a file in a particular drive?

Any help appreciated.

---

### Post by slickymaster on 2013-04-18
Hi jkdunne, welcome to the forums.

You can define samba share permissions as you want. See [this]("http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html").

---

