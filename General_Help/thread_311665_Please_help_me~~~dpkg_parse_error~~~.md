---
title: "Please help me~~~dpkg parse error~~~"
date: 2006-12-03
forum: General Help
---

### Post by leesshmily on 2006-12-03
I have a problem need to help.
When i try to install a language support, there is a error.
It shows like "dpkg parse error, in file '/var/lib/dpkg/available' near line 1: EOF after name ' ' ", and "E: Sub-process /usr/bin/dpkg returned an error code (2)". The system also told me "A package failed to install. Try to recover;" 
Is there anyone knows how to fix it? My system is Ubuntu Edgy.
Thanks a lot.

---

### Post by leesshmily on 2006-12-03
](*,) Help~~~~~~~~

---

### Post by lamego on 2006-12-03
1) make sure you don't have unsafe entries on your sources.list.
2) Open a terminal and type:
```
sudo apt-get update
```

---

