---
title: "Not privileged to mount drives?"
date: 2008-04-30
forum: General Help
---

### Post by Rusty023 on 2008-04-30
My drives decided they didn't want to mount, so I used the NTFS config tool, and now it says I'm not privileged. What's the go? Do I have to become root or can I fix this?

---

### Post by bodhi.zazen on 2008-04-30
Either add an entry in fstab or :

```
gksu ntfs-config
```

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by woocashacn on 2008-04-30
> **Rusty023 said:**
> My drives decided they didn't want to mount, so I used the NTFS config tool, and now it says I'm not privileged. What's the go? Do I have to become root or can I fix this?

Not clearly closed Windows session? Hibernated?

---

