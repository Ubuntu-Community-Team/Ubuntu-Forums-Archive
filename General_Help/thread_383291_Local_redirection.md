---
title: "Local redirection?"
date: 2007-03-13
forum: General Help
---

### Post by robinl on 2007-03-13
I have dyndns, LAMP, the works set up and installed phpBB2. However it requires a domain name to redirect pages to, which if I want to access it I have to set it to 127.0.0.1 or localhost while if I want my friends to see it I would have to set it to [example.com]. Is there a way to sidestep this or to redirect [example.com] to localhost locally on my computer?

---

### Post by Jussi Kukkonen on 2007-03-13
```
127.0.0.1 www.example.com

```
in /etc/hosts

---

### Post by robinl on 2007-03-13
Thanks a lot, exactly what I needed

---

