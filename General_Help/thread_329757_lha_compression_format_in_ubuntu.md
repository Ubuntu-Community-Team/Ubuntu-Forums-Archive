---
title: "lha compression format in ubuntu"
date: 2007-01-02
forum: General Help
---

### Post by kiratsuki on 2007-01-02
I am using Japanese version of Ubuntu 6.10. However, from what I've already tried, I am not able to extract .lzh archives. (I am trying to run a script for an image board.)  I've tried to use both the Extraction Manager and Ark. After these didn't work, I goggled it and got back this document[http://www-128.ibm.com/developerworks/library/l-lw-comp.html#h2]("http://www-128.ibm.com/developerworks/library/l-lw-comp.html#h2")

In it, it recommends that I type in an lha command with various options and combinations, but this command does not work (it says there is no lha command). :confused:  It says it was ported to Linux however, so, perhaps there is something I am missing? This particular format is very popular in Japan, so I think it would be useful to have for a Japanese operating system... So maybe someone has figured out a way to do this?

Kira

---

### Post by zanglang on 2007-01-02
Maybe you don't have it installed. Try:
```
sudo aptitude install lha
```

---

