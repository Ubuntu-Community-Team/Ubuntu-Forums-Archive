---
title: "[SOLVED] Java apps doesn't show dead key chars"
date: 2008-06-13
forum: General Help
---

### Post by ffurlanete on 2008-06-13
The java text editors I've tried (actually only the swing ones) doesn't show dead key chars like "'áéç...

I've tried both sun-java-6 and openjdk-6. Also I've tried both us and us-intl keyboard layouts.

Im using ubuntu 8.04 on a sony vaio tz.

Thanks in advance.

---

### Post by ffurlanete on 2008-06-14
Humm, I was using scim. It was related to the #98890 bug.
I just added my locale (pt_BR.UTF-8 ) to /etc/scim/global and it worked.

---

