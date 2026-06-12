---
title: "sensors does not show fan speed with new kernel (2.6.24-16-generic)"
date: 2008-05-09
forum: General Help
---

### Post by akudewan on 2008-05-09
Hi,

After upgrading to hardy, lm-sensors is not showing me the fan speed (and a lot of other thermistor temperatures), despite running sensors-detect again.

I have an NVidia nForce 610i board. Wondering if I should file a bug report. Has anyone else faced this ?

---

### Post by PmDematagoda on 2008-05-09
Did you try running:-
```
sudo sensors-detect
```
again?

---

### Post by akudewan on 2008-05-09
Yes, I did. It gives me the same two chip drivers as the previous kernel:
```

it87
coretemp

```

---

