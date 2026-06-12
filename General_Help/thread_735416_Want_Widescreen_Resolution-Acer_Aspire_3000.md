---
title: "Want Widescreen Resolution-Acer Aspire 3000"
date: 2008-03-25
forum: General Help
---

### Post by Takido on 2008-03-25
Hello. I installed ubuntu recently and i screwed it up using xserver to try to add a widescreen resolution. I have a crappy SiS integrated laptop graphics card. All that i want is to get 1280x800 wide screen easily without screwing up my machine like before( i had to re-install it.) any way to easily do this without ruining my computer?

---

### Post by warp99 on 2008-03-25
Run the following:

```
sudo dpkg-reconfigure xserver-xorg
```

This will create a new xorg.conf file and you can choose the resolution you would like to use. ;)

---

