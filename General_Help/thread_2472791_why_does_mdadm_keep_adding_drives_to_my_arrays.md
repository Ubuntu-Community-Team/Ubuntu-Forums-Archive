---
title: "why does mdadm keep adding drives to my arrays?"
date: 2022-03-12
forum: General Help
---

### Post by alexloz on 2022-03-12
I recently upgraded to Ubuntu 20.04.4.

For some reason, when I manually fail a drive from an array, and remove it, some job (with no output to any logs I can find) adds it back in on its own, causing all sorts of problems. Does anyone know what I can look into to figure out why it's doing that?

It's doing the same if I manually --stop an array, it reassembles it behind my back, at seemingly random intervals.

---

