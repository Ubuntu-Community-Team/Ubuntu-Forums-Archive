---
title: "How do I find my internal IP?"
date: 2007-04-28
forum: General Help
---

### Post by noerrorsfound on 2007-04-28
How do I find my internal IP?

---

### Post by taurus on 2007-04-28
You mean something like this.

Applications -> Accessories -> Terminal
```
/usr/sbin/ifconfig
```

---

### Post by klato on 2007-04-28
You could also right-click on networkmanager (if you use it), and hit Connection Information

---

### Post by noerrorsfound on 2007-04-28
> **taurus said:**
> You mean something like this.

Applications -> Accessories -> Terminal
```
/usr/sbin/ifconfig
```

bash: /usr/sbin/ifconfig: No such file or directory

---

### Post by taurus on 2007-04-28
Maybe it's in /sbin.

```
/sbin/ifconfig
```

---

### Post by OffHand on 2007-04-28
```
ifconfig -a
```

---

### Post by bluesonix on 2007-04-29
System > Administration > Network > Select which interface's IP address you want > Properties 

Hope this helps. :)

---

