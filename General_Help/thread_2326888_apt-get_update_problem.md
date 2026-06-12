---
title: "apt-get update problem"
date: 2016-06-05
forum: General Help
---

### Post by starcruser2598 on 2016-06-05
I typed in the command "apt-get update" into my terminal {without the woutations obviously} and it returned:E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)E: Unable to lock directory /var/lib/apt/lists/E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?I have ubuntu installed on my hp chromebook through crouton. Any way to fix this?

---

### Post by jeremy31 on 2016-06-05
Have you tried ```
sudo apt-get update
```

What exactly is crouton?

---

### Post by starcruser2598 on 2016-06-05
I forgot sudo.

---

### Post by gsahli on 2016-06-05
try sudo apt-get update?

---

### Post by starcruser2598 on 2016-06-05
crouton is how I installed ubuntu onto the chromebook, it was made by a google worker. and I just forgot sudo. thank you though

---

