---
title: "How do I login automatically?"
date: 2019-02-28
forum: General Help
---

### Post by jians5 on 2019-02-28
Using cinnamon. I've gone though every result on the first page of google. They all tell me to go add [autologin-user=*username] to */etc/lightdm/lightdm.conf. When I do so I can't boot.

I'm obviously changing "username" to my username.

---

### Post by deadflowr on 2019-02-28
Are you placing brackets around the autologin line?

---

### Post by jeremy31 on 2019-02-28
My /etc/lightdm/lightdm.conf contains
```
[SeatDefaults]
autologin-user=jeremy
```

And auto login works in Ubuntu 18.04 Cinnamon

---

