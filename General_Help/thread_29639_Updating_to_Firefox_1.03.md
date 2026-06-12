---
title: "Updating to Firefox 1.03"
date: 2005-04-25
forum: General Help
---

### Post by fparri on 2005-04-25
I would like to update firefox in my Hoary to 1.03, Italian language.
What is the best way to perform this update?

---

### Post by Burgundavia on 2005-04-25
Most of the security fixes in 1.0.3 have already been backported to 1.0.2 in hoary, so you don't need to worry about that.

Corey

---

### Post by fparri on 2005-04-26
Thanks, good news  :smile:

---

### Post by weissnich on 2005-04-26
another way is to change your sources.list
to debian unstable,
apt-get update, apt-get install and then switch back to ubuntu
that is how I did it

---

### Post by fng on 2005-04-27
i dont recommand mixing debian unstable and ubuntu repositories!

---

### Post by nocturn on 2005-04-28
[QUOTE=Burgundavia]Most of the security fixes in 1.0.3 have already been backported to 1.0.2 in hoary, so you don't need to worry about that.

Corey[/QUOTE]

Yes, but one of the most serious (javascript local file compromise) is not backported!

---

