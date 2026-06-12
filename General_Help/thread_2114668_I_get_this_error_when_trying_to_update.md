---
title: "I get this error when trying to update"
date: 2013-02-10
forum: General Help
---

### Post by TimEnid on 2013-02-10
```
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

any suggestions?

I was trying to update and it just got stuck on "applying changes"

---

### Post by ibjsb4 on 2013-02-10
You can have only one package manager open at a time.  A package manager will lock processes and will not be available to the system.

---

### Post by Bufeu on 2013-02-10
If you have Synaptic or an other package manager open, close it.

---

### Post by TimEnid on 2013-02-10
> **ibjsb4 said:**
> You can have only one package manager open at a time.  A package manager will lock processes and will not be available to the system.

i dont have anything else open.

---

### Post by ibjsb4 on 2013-02-10
Manually remove the lock.

```
sudo rm /var/lib/apt/lists/lock
```

and then try an update

```
sudo apt-get update
```

---

### Post by Bufeu on 2013-02-10
> **TimEnid said:**
> i dont have anything else open.
Then manually remove the lock with ```
sudo rm /var/lib/apt/lists/lock
``` Then do an update with ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by TimEnid on 2013-02-10
> **ibjsb4 said:**
> Manually remove the lock.

```
sudo rm /var/lib/apt/lists/lock
```

and then try an update

```
sudo apt-get update
```

got it. thanks.

---

### Post by ibjsb4 on 2013-02-10
nice  ):P

---

