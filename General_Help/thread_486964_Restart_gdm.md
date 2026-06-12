---
title: "Restart gdm?"
date: 2007-06-28
forum: General Help
---

### Post by gr1Mo on 2007-06-28
dlt

---

### Post by bodhi.zazen on 2007-06-28
Sounds like you need to reconfigure X ...

Did you by chance install something like the nvidia or ati driver and then update the kernel ?

If so you need to re-install the driver then re-start gdm

Also it would help if you could post any error message.

Do this : ```
sudo /etc/init.d/gdm stop
startx
```

Post any error messages please...

---

### Post by gr1Mo on 2007-06-28
asd

---

### Post by gr1Mo on 2007-06-28
asd

---

### Post by gr1Mo on 2007-06-28
delete.

---

### Post by bodhi.zazen on 2007-06-28
Sorry, yea reinstalling the nvidia driver would be where I would start :)

---

