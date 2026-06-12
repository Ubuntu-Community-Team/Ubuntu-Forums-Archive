---
title: "how to get APT to ignore upgrading packages"
date: 2006-08-05
forum: General Help
---

### Post by baldy1324 on 2006-08-05
hi i would like to know if there is a way in apt (or whatever front-end that applies to apt) that can ignore upgrading a certain package (kernel).
thank you

---

### Post by Jagot on 2006-08-05
```
aptitude hold pkgname
```

---

### Post by der_joachim on 2006-08-06
Either apt-hold or apt-pinning. [This]("http://jaqque.sbih.org/kplug/apt-pinning.html") is a good guide to apt-pinning for a debian, but still applicable.

---

### Post by baldy1324 on 2006-08-14
can you please help me find i guide on how to use apt-hold or tell me if aptitude hold package will apply to apt and its frontends.
thank you

---

