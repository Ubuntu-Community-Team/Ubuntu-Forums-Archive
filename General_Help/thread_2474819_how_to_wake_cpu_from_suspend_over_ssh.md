---
title: "how to wake cpu from suspend over ssh"
date: 2022-05-09
forum: General Help
---

### Post by buill on 2022-05-09
hi wol sometimes works but if my ubuntu is off for long periods of time wol stops working im not sure why of it it is a router or laptop issue but i can suspend with cmd 

```
sudo systemctl suspend
```

but how can you wake over ssh from this state? thanks

---

### Post by TheFu on 2022-05-09
You cannot.
WoL is required to work.

---

