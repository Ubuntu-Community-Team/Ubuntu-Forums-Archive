---
title: "How to unable Bluetooth at startup/restart?"
date: 2022-08-10
forum: General Help
---

### Post by jl2414 on 2022-08-10
I have version Focal Fossa 22.04.1, on a Dell laptop,
By defalt my Blotooth turn on at start and restart.

Is there a way to disable Bluetooth at start and restart?

---

### Post by psychohermit on 2022-08-10
```

sudo systemctl disable bluetooth

```

--glenn

---

### Post by jl2414 on 2022-08-13
Thanks a lot.
I hope I can turn it on in the top right corner again (next to sound, micro, brightness etc.)... :confused:
I'm not so well rounded in Ubuntu yet... :D

---

### Post by mIk3_08 on 2022-08-14
> **jl2414 said:**
> Thanks a lot.
I hope I can turn it on in the top right corner again (next to sound, micro, brightness etc.)... :confused:
I'm not so well rounded in Ubuntu yet... :D

Try to run the reverse command in terminal just change the disable to enable. Regards and cheers
```
sudo systemctl enable bluetooth
```

---

