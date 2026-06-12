---
title: "Java Rutime Plugin"
date: 2007-01-19
forum: General Help
---

### Post by bootslap on 2007-01-19
While browsing Firefox prompted to get a plugin for java runtime. I tried to get one, but it asked me to download manually. Once I downloaded, I realized that is is .rpm. How do I intall it into firefox as a plugin?

---

### Post by taurus on 2007-01-19
```
sudo aptitude update
sudo aptitude install alien
alien **filename**.rpm
sudo dpkg -i **filename**.deb
```

---

