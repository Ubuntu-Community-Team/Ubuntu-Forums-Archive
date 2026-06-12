---
title: "where can i find the 2.6.17.1 image for i386?"
date: 2007-01-23
forum: General Help
---

### Post by Newlad on 2007-01-23
i need to make a DVR application,the card need 2.6.17.1 kernel install,it need Feb5 install also,
but i want to do it in ubuntu 7.04,where can i find the 2.6.17.1 image ? or how can i build it ?

thanks very much

---

### Post by ~LoKe on 2007-01-23
```
sudo apt-get install linux-image-2.6.17-10-386
```
Or, preferably:
```
sudo apt-get install linux-image-2.6.17-10-generic
```

---

### Post by flixer on 2007-01-23
I'm just wondering. Doesn't your application support 2.6.17.1 or higher?

---

