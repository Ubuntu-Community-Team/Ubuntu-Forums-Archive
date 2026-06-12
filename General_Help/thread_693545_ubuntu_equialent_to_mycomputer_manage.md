---
title: "ubuntu equialent to mycomputer manage?"
date: 2008-02-11
forum: General Help
---

### Post by aimhigher101 on 2008-02-11
Hi i normally use windows so im not that good with the ubuntu os so thought i'd ask you guys. In the windows os you can right click on my computer and go onto manage and see whats on your computer and if the drivers are installed correctly and that they are working. I was wondering is there a way to do this on Ubuntu (i have version 7.10 workstation)?
thanks

---

### Post by TitanKing on 2008-02-11
> **aimhigher101 said:**
> Hi i normally use windows so im not that good with the ubuntu os so thought i'd ask you guys. In the windows os you can right click on my computer and go onto manage and see whats on your computer and if the drivers are installed correctly and that they are working. I was wondering is there a way to do this on Ubuntu (i have version 7.10 workstation)?
thanks

Normally all drivers would be installed and configured already, however you could:

See if there is any drivers that still requires installation by going >System>Administration>Restricted Driver Manager. All needs to be "green" if any are listed there.

For more specific details:
System>Preferences>Hardware Information

Regards

---

### Post by jan quark on 2008-02-11
well

try this perhaps it suits your needs

go to system > administration > system monitor
go to system > preferences > hardware information

run in terminal
```

lsmod
```

this will show you the loaded and active modules

to view the running processes
run
```

top
```

in terminal

---

### Post by hyperair on 2008-02-11
Don't forget ```
sudo lshw
lspci
lsusb
```

---

