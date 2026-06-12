---
title: "[SOLVED] command line inquiry"
date: 2008-02-01
forum: General Help
---

### Post by yazuki101 on 2008-02-01
i was wondering if there was a way to see whether or not I am connected to the internet, while I am in recovery mode. Unfortunately I cannot get into the GUI

---

### Post by erfahren on 2008-02-01
you could just try pinging google
```

ping -c4 www.google.com

```
or with its IP address
```

ping -c4 208.69.32.230

```

---

### Post by Rocket2DMn on 2008-02-01
I don't believe recovery mode has internet access, but using ping as shown above will show you.

---

### Post by yazuki101 on 2008-02-01
can anyone think of any other reason i would recieve this message after an 'apt-get update'
-"Could not resolve 'ca.archive.ubuntu.com'"

---

### Post by yazuki101 on 2008-02-01
after trying to ping google using the numerical ip, it came back 'connect: Network is unreackable'

Also, wouldn't recovery mode need internet access in order acquire the 'apt-get update' as well as the nvidia drivers i need

---

### Post by hahahan on 2008-02-01
In my case network works fine when I boot recovery-mode.
Does "ifconfig -a" show any interfaces?

regards

---

