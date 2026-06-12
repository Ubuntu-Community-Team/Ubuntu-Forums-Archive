---
title: "Windows does not show up in grub menu."
date: 2013-01-11
forum: General Help
---

### Post by twtduck.ii on 2013-01-11
I cannot select windows from the grub boot menu, but all the other options are available. I already ran windows boot repair, then ubuntu boot repair, but I can only run one either way. 

Information on my system can be found here.
[http://paste.ubuntu.com/1520650/](http://paste.ubuntu.com/1520650/)
 Please tell me what i can do to fix this problem. It's very important that both systems are functional. 
Thank you,
Twtduck.ii

---

### Post by lukeiamyourfather on 2013-01-11
Have you tried this from Ubuntu?

```
sudo update-grub
```

---

### Post by rrich1974 on 2013-01-11
go to windows, install latest easyBCd, create a new entry, and install grub (from easyBCD) on ubuntu partition. that is the easyest way, i guess.....

---

### Post by lukeiamyourfather on 2013-01-11
> **rrich1974 said:**
> go to windows, install latest easyBCd, create a new entry, and install grub (from easyBCD) on ubuntu partition. that is the easyest way, i guess.....

I've also used EasyBCD, great program!

---

