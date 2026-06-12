---
title: "chsh did not change my shell. Why?"
date: 2013-05-17
forum: General Help
---

### Post by postt on 2013-05-17
I tried to use chsh to change my shell to bash:

```
~ % chsh -s /bin/bash



```

But my shell remains unchanged afterwards:

```
~ % echo $SHELL      
/bin/zsh

```
What went wrong?

---

### Post by schragge on 2013-05-17
As chsh changes the *login* shell you probably need to log out and log in again for the change to take effect.

---

### Post by postt on 2013-05-17
Never mind. I just realized I needed to reboot the computer for the change to take effects.

---

### Post by postt on 2013-05-17
> **schragge said:**
> As chsh changes the *login* shell you probably need to log out and log in again for the change to take effect.

We just posted at the same time. I rebooted the computer and it's working now. I"m sure log out and log in again would work too. Thanks!

---

