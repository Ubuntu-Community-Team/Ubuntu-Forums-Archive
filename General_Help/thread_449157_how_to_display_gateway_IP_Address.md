---
title: "how to display gateway IP Address"
date: 2007-05-19
forum: General Help
---

### Post by Klitzie on 2007-05-19
Wat us the equivalent of** ipconfig/all**  in Ubuntu in displaying IP  ADDRESS, Subnet Mask and Gateway Address?

---

### Post by mapalma on 2007-05-19
ifconfig ;)

---

### Post by Bachstelze on 2007-05-19
Address and netmask :

```
sudo ifconfig -a
```

Kernel routing table :

```
sudo route
```

---

### Post by kh4nh on 2007-05-19
```
sudo ifconfig -a
```

# the a switch will display all the interfaces even the down ones.

---

