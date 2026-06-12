---
title: "gcc not found"
date: 2007-03-17
forum: General Help
---

### Post by luke.frag on 2007-03-17
Hi,

I have a problem with already installed system. Ubuntu claims gcc is not installed, it can not be found anywhere and simply trying to run "gcc" in terminal gives a message about unknown command. I know it's probably impossible for a system not  to have gcc installed by default, i never checked it after install until yesterday. I need it to get my network working so getting packages by network is not a solution here.
My question is, is it possible for a clean normal install not to have gcc and if yes how should i get it if i have no networking?

Thank you in advance for help.

---

### Post by taurus on 2007-03-17
You need the build-essential package.  Insert the Ubuntu install CD into the driver and do

Applications -> Accessories -> Terminal
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by luke.frag on 2007-03-18
Thank you. It worked and by knowing this method i also got to install some more stuff and got my internet connection running :)

---

