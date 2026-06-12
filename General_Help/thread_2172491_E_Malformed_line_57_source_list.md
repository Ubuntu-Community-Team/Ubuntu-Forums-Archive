---
title: "E: Malformed line 57 source list"
date: 2013-09-05
forum: General Help
---

### Post by frederik-f on 2013-09-05
Hey guys. I'm trying to $ sudo apt-get update but get this error.

E: Malformed line 57 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.

I tried to search on Google but couldn't really find a solution for line 57, only some of the other lines.

---

### Post by bluefrog on 2013-09-05
sudo nano /etc/apt/sources.list

correct line 57 and other offending lines if necessary

should basically read

deb [http://whatever.com/ubuntu](http://whatever.com/ubuntu) precise main

---

### Post by frederik-f on 2013-09-05
> **bluefrog said:**
> sudo nano /etc/apt/sources.list

correct line 57 and other offending lines if necessary

should basically read

deb [http://whatever.com/ubuntu](http://whatever.com/ubuntu) precise main

Thanks that did it.

---

