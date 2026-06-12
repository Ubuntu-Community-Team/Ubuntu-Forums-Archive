---
title: "Synaptic error message"
date: 2007-06-15
forum: General Help
---

### Post by Old *ix Geek on 2007-06-15
Whenever I install anything via synaptic, the following message appears in the terminal window:

**Not all changes and updates succeeded.  For further details of the failure, please expand the 'terminal' panel below**

The thing is...there ISN'T a 'terminal panel' below!  Anyone have any idea what this is referring to?

---

### Post by southernman on 2007-06-15
There will be, on the lower left side, the word Details - with an arrow on the side of it. Click that and it will open "expand" the terminal window below.

---

### Post by Old *ix Geek on 2007-06-15
Thanks, but no, there isn't (or I'm blind as a bat...which, at my age, could be the case!).  Here's a screenshot I just took:

[img]http://www.smartassproducts.com/images/Synaptic_error.jpg[/img]

---

### Post by zvacet on 2007-06-16
```
sudo dpkg --configure -a
```

---

### Post by Old *ix Geek on 2007-06-16
> **zvacet said:**
> ```
sudo dpkg --configure -a
```
I've already done that...numerous times.  :(

---

