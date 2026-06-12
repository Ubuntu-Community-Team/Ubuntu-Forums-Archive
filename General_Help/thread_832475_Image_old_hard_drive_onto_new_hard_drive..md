---
title: "Image old hard drive onto new hard drive."
date: 2008-06-17
forum: General Help
---

### Post by stchman on 2008-06-17
Hello, I just bought a new SATA 750GB hdd.

My old hdd has both XP and Ubuntu on it and I want to simply copy the XP and Ubuntu partition over to the new hdd.

I understand that gparted can do this very easily.

Are there any tutorials to copy the partitions over and make sure GRUB works correctly as well?

Thanks.

---

### Post by rraj.be on 2008-06-17
To colone entire patrtition you can use partimage

sudo apt-get install partimage

Here is good link of HOW TO CLONE HARD DISK PARTITION>

```
[[COLOR="Blue"]http://pittman.ws/articles/howto/partimage.html[/COLOR]]("http://pittman.ws/articles/howto/partimage.html")
```


the biggest advantage of partimage is that


It will copy only used space.

---

### Post by logos34 on 2008-06-17
[http://gparted.sourceforge.net/larry/move/move.htm](http://gparted.sourceforge.net/larry/move/move.htm)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

