---
title: "ubuntu package for perl ODF::lpOD?"
date: 2021-04-03
forum: General Help
---

### Post by turtles on 2021-04-03
Hello 
Is there an ubuntu package for perl ODF::lpOD?
Or a should it be installed with cpan?
This is on a minimal headless server.
Thanks in advance

---

### Post by turtles on 2021-04-05
To answer my own question I needed to:
apt-get install build-essential
apt-get install libfile-type-perl
Then in cpan I installed
 install ODF::lpOD

---

