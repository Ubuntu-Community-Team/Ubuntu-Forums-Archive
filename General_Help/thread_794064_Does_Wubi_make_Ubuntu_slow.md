---
title: "Does Wubi make Ubuntu slow?"
date: 2008-05-14
forum: General Help
---

### Post by tgilliam on 2008-05-14
Today I installed Ubuntu via Wubi, everything is fine. Its just that everything runs slow, my fan is loud. So im guessing its my CPU?


512mb ram
2.79 celeron

---

### Post by DieB on 2008-05-14
cpu seems ok, but you got some speciallities while yousing wubi.

first its layin on a ntfs formatted disk (not that fast cause not that long supported).
second as far as i understood acpi and things like that aint work due to abstraction layer.

---

### Post by ago on 2008-05-14
In theory not, but you can run some benchamrking programs or use things like top to find out bottlenecks. In particular check swap usage and disk I/O activity, as well as the ntfs process.

---

