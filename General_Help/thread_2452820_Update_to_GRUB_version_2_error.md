---
title: "Update to GRUB version 2 error"
date: 2020-10-28
forum: General Help
---

### Post by mickee384 on 2020-10-28
when doing a normal update I came across the update to GRUB EFI AMD64 that has unmet dependencies. I had no choice but to deselect this update. Any one else have this error in latest posted updates? What dependencies are they talking about? It is referring to ```
grub-efi-amd64-signed: 
```

---

### Post by CharlesA on 2020-10-29
Do you get any output when you run this command?

```
sudo apt upgrade
```

It should tell you which dependency is missing and why it is unable to resolve it.

---

### Post by mickee384 on 2020-10-29
It seems to have fixed itself today. Sorry to bother you!

---

