---
title: "Procedure for making apt aware of programs installed from source"
date: 2006-11-06
forum: General Help
---

### Post by Roobert on 2006-11-06
How do I make apt aware of programs that I've compiled and installed myself? I want ensure dependency-checking and everything else that apt does.

Thanks!

---

### Post by ahaslam on 2006-11-06
Use checkinstall (it's in the repo's)

Instead of sudo make install, use sudo checkinstall

Tony

---

### Post by Roobert on 2006-11-06
Great, thanks. I'll check it out.

---

