---
title: "/etc/sudoers.d/README Permission Denied"
date: 2016-03-21
forum: General Help
---

### Post by kenneth20 on 2016-03-21
Hi, 

Every time I do sudo ls, or sudo whatever. I get the command, but, I also get a message that says "/etc/sudoers.d/README permission denied. 

How can I fix that?

---

### Post by steeldriver on 2016-03-21
Have you looked at the file's actual permissions?

```

ls -l /etc/sudoers.d/

```

---

