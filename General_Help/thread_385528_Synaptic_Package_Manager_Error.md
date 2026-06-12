---
title: "Synaptic Package Manager Error"
date: 2007-03-15
forum: General Help
---

### Post by jbernhardt on 2007-03-15
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

I get this error when I start up synaptic package manager. I cannot use it for anything now. Please help.

---

### Post by Kateikyoushi on 2007-03-15
Run the terminal from applications > system tools and copy paste the following command there.

```
sudo dpkg --configure -a
```

---

### Post by jbernhardt on 2007-03-15
Ahh, thank you. Turns out I closed my Open TTD install terminal a bit too early.

---

