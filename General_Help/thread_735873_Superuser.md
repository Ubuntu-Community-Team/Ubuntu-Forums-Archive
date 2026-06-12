---
title: "Superuser"
date: 2008-03-26
forum: General Help
---

### Post by Mojo99 on 2008-03-26
When I try to download Ubuntu updates I get a message "Error - dpkg was interupted - you need to run 'dpkg --configure -a" to correct the problem.

When I run this command in a terminal I get s message "superuser privilege required"  I have enabled all privileges on my user which is the only user on my PC.

How do I get to Superuser status or how do I fix this problem?

---

### Post by zvacet on 2008-03-26
```
sudo dpkg --configure -a
```

---

### Post by Mojo99 on 2008-03-26
You are a genius!

Command run.

Updates dowloaded.

Problem solved.

A million thanks.

Regards,

Mojo

---

