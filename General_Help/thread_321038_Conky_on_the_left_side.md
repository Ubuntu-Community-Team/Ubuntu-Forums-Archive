---
title: "Conky on the left side"
date: 2006-12-18
forum: General Help
---

### Post by blonder on 2006-12-18
In the moment my conky starts on the right side from my Desktop,but i want conky on the left side.How can i do this ?

---

### Post by taurus on 2006-12-18
Look in ~/.conkyrc and there is an option to start it either on the top left, bottom left, top right, or bottom right.  Just pick the corner you want, save it, and restart it.

Applications -> Accessories -> Terminal
```
gedit ~/.conkyrc
```

---

### Post by blonder on 2006-12-18
Is this right place ?

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

---

### Post by taurus on 2006-12-18
Exactly.

---

