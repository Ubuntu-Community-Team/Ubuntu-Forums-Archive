---
title: "libx32 and lib32"
date: 2016-01-19
forum: General Help
---

### Post by monkeybrain20122 on 2016-01-19
I notice in Vivid there are two directories under / called libx32 and lib32 with basically the same contents, but in Wily there is only lib32. What is the difference between lib32 and libx32? Thanks.

---

### Post by mc4man on 2016-01-19
I believe in a default install there would be no /libx32 but it could show up via certain package installs.
Ex. here on 14.04 (amd64 install), there was no /libx32 dir. When I installed libc6-x32 it was created & populated. 
Could be from you installing some build related packages or any libx32* package, search libx32 in synaptic..

---

