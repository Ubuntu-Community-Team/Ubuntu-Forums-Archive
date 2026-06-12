---
title: "enabling ssh"
date: 2007-10-30
forum: General Help
---

### Post by mszl_1 on 2007-10-30
how do i enable ssh on my machine. i have tried" sudo apt-get install openssh" but it failed to work?!! any ideas
thanks

---

### Post by jfordwashere on 2007-10-30
Instead of openssh, try "sudo apt-get install ssh"

---

### Post by taurus on 2007-10-30
```
sudo apt-get update
sudo apt-get install openssh-server
```

---

