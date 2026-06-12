---
title: "Real Player File Stuck On Desktop / Root Permission Problem"
date: 2007-09-18
forum: General Help
---

### Post by Niall Stephen on 2007-09-18
n00b question ... 

I've successfully installed Real Player & it works fine. However during the installation process I think I put the Real Player file in the wrong location & now it's stuck on my desktop and refuses to be moved somewhere else. Permissions says the owner is root. 

The file is called RealPlayer & the icon has a little locked padlock. I just want to stick it in my niall home folder to get it off the desktop but it refuses to budge. 

Any ideas ? I'm sure it's idiotically simple but I haven't a clue ... thanks in advance for your help ! :)

---

### Post by dcstar on 2007-09-19
> **Niall Stephen said:**
> n00b question ... 

I've successfully installed Real Player & it works fine. However during the installation process I think I put the Real Player file in the wrong location & now it's stuck on my desktop and refuses to be moved somewhere else. Permissions says the owner is root. 

The file is called RealPlayer & the icon has a little locked padlock. I just want to stick it in my niall home folder to get it off the desktop but it refuses to budge. 

Any ideas ? I'm sure it's idiotically simple but I haven't a clue ... thanks in advance for your help ! :)

Do this in a terminal and you can then have root permissions to move it (and reset its permissions):
```
sudo nautilus
```

---

### Post by Niall Stephen on 2007-09-19
Eureka !! Now my desktop is totally as I want it 

Cheers, David, very much appreciated :)

---

