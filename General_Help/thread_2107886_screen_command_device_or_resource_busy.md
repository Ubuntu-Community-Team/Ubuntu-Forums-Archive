---
title: "screen command: device or resource busy"
date: 2013-01-23
forum: General Help
---

### Post by gsedsd on 2013-01-23
Hello,

I'm trying to use screen command to read from serial port. It works perfectly but only under superuser profile (with sudo).

```
sudo screen /dev/ttyS0
```

if I don't use sudo it works only the first time.

```
screen /dev/ttyS0
```

if I close it with [ctrl+a] [ctrl+d] or just close the terminal the second time I get the error

```
device or resource busy
```

user was added to dialout group
why can it be so?

---

### Post by gsedsd on 2013-01-23
```
lsof /dev/ttyS0
```

showed that screen still used the port, just killed it

solved

---

