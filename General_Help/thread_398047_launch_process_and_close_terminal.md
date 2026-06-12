---
title: "launch process and close terminal"
date: 2007-03-31
forum: General Help
---

### Post by jmvidalvia on 2007-03-31
I was told that adding "&" to a command, it will run in a second level, so I could close the terminal I used to launch it.
I could always check if it is running with: ps
I am trying it with wvdial: it is anoyying to leave the terminal opened while connect.
¿how can I get it?
My command is:
sudo wvdial huawei internet

Many thanks!

---

### Post by Ramses de Norre on 2007-03-31
This will do:
```
nohup sudo wvdial huawei internet &
```
All output will be in ~/nohup.out and you can safely close the terminal. Nohup is specifically designed for this purpose, mostly for running services over remote connections.

---

### Post by jmvidalvia on 2007-03-31
nohup works great!
Thank you very much!

---

### Post by jmvidalvia on 2007-03-31
¿?

---

