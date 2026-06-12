---
title: "Format swap space??"
date: 2012-11-05
forum: General Help
---

### Post by kharontes on 2012-11-05
For format  i left my swap space  and  just  deleted  os and  reinstalled after format  my laptop is flying  just like a plane :mad: 
i checked at gparted it says unknown and i cant form swap space.
how can i fix it?

---

### Post by oldfred on 2012-11-05
You do not format swap. It is just space allocated for RAM overflow.

If you encrypted /home, swap is also encrypted and gparted cannot see it and shows it as unknown.

---

