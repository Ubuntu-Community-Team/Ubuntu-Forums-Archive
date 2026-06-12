---
title: "Pkg-config cannot find sdl2"
date: 2022-04-03
forum: General Help
---

### Post by artie1977 on 2022-04-03
Hi,
I'm on Ubuntu 20.10 and am trying to build custom image with yocto. I'm getting an error: pkg-config cannot find sdl2. How can I install that package?

Thank you

---

### Post by Impavidus on 2022-04-03
You probably need the development version of the package:```
sudo apt install libsdl2-dev
```

---

### Post by deadflowr on 2022-04-03
20.10?
That release hit end of life.

Are you sure?

---

