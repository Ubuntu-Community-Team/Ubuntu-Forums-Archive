---
title: "What is ep_pol and why doesn't my Gentoo system give it for urxvt?"
date: 2019-05-18
forum: General Help
---

### Post by dman7773 on 2019-05-18
When I spawn a urxvt terminal in Ubuntu Xenial, I get two processes:

```
       
4    0 S one       5252  5036  1  80   0 - 24479 ep_pol 22:46 pts/1    00:00:00 urxvt -bg rgba:0000/0000/0000/dddd        
5    1 S one       5253  5252  0  80   0 - 20946 unix_s 22:46 pts/1    00:00:00 urxvt -bg rgba:0000/0000/0000/dddd

```

On my Gentoo system, I only get one. 

Ubuntu seems to have a extra ep_pol process that my Gentoo system does not have. What is ep_pol and why does Ubuntu have it and not Gentoo?

---

