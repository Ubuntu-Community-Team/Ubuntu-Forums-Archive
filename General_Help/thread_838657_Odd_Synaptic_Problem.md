---
title: "Odd Synaptic Problem"
date: 2008-06-23
forum: General Help
---

### Post by Tiger658 on 2008-06-23
Hi I am having a weird problem, for some reason I can't open Synaptic, when I try to open it, the little thing on the tool bar pops up that says "Opening Administrative Application," then after a while it goes away, and doesn't open, also when I try to use the update manager, I click "Install Updates" and it goes grey and doesn't do anything, it is driving me crazy, I can't update my system, or install any other packages, PLEASE HELP!!!!!!!!

Thanks,
Tiger

---

### Post by ibutho on 2008-06-23
What happens when you run Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude safe-upgrade

```

---

### Post by Tiger658 on 2008-06-23
Thank You it worked. What exactly did that code do?

Thanks Again,
Tiger

---

### Post by ibutho on 2008-06-23
The first command updates the software sources and then the second upgrades the packages.

---

