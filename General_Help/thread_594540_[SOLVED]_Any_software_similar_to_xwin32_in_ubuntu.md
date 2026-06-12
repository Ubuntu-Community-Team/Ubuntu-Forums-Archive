---
title: "[SOLVED] Any software similar to xwin32 in ubuntu?"
date: 2007-10-28
forum: General Help
---

### Post by nastavirss on 2007-10-28
I need to run some applications that is over xwin32 in windows in ubuntu.

Can anyone suggest anything similar to xwin32 in ubuntu.

---

### Post by nastavirss on 2007-10-28
sorry. found that it can be done using ssh -X ip

---

### Post by hikaricore on 2007-10-28
I'm not sure if this is exactly what you're looking for, but if you install an SSH server (openssh should do the trick), you can ssh into the box with the -X flag and run applications remotely.

```
ssh -l username -p portnumber -X machineaddress
```

---

### Post by hikaricore on 2007-10-28
Glad you got it.  ^_^

Best of luck.

---

