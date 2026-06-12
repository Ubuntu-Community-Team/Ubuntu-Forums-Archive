---
title: "[SOLVED] Deleteing not needed .deb files"
date: 2007-08-24
forum: General Help
---

### Post by Patrick793 on 2007-08-24
How can I delete the .deb files from /var/cache/apt/archives?
I know they are not needed, so how do I remove them? I'm new to Ubuntu, and don't know that much code in the terminal. I think you have to delete them from the terminal. But anyway, please help.

Thanks
-Patrick

---

### Post by anubhavrocks on 2007-08-24
```
sudo apt-get clean
```

---

### Post by Patrick793 on 2007-08-24
> **anubhavrocks said:**
> ```
sudo apt-get clean
```

Thank you.

---

