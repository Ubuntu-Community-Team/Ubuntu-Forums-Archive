---
title: "telnet"
date: 2008-01-03
forum: General Help
---

### Post by ladybluballs on 2008-01-03
I need to know how I can run a telnet command to another linux box I have on my network ubuntu is on my main computer

---

### Post by sciencewhiz on 2008-01-03
in a terminal run:

```
telnet host
```

There are a lot more options, which you can read about with ```
man telnet
```

---

### Post by taurus on 2008-01-03
Try using ssh instead.  It's better and more secure than telnet.

```
ssh -l login_name ip_address
```

---

### Post by ladybluballs on 2008-01-03
> **taurus said:**
> Try using ssh instead.  It's better and more secure than telnet.

```
ssh -l login_name ip_address
```

dang I just cant seem to get the hang of how this is done I think I just permently added something like a host ip address that did not work

---

