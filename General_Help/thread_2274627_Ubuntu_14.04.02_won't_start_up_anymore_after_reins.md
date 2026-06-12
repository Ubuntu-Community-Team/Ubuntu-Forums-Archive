---
title: "Ubuntu 14.04.02 won't start up anymore after reinstalling lightdm. Black screen"
date: 2015-04-21
forum: General Help
---

### Post by sebastiaan5 on 2015-04-21
So I had some issues with ubuntu, my ubuntu won't start up properly I had to type my password twice, first it was a weird log im screen with no data, no option to power off. Second log in screen was normal. 

This is due to pc crash while having graphic card enabled, playing minecraft while not connected to power grid, i mean playing on pc battery. 

So i looked up on the net and the most frequent feedback was reinstalling lightdm with the command:

sudo apt-get purge lightdm && sudo apt-get install lightdm

Everytime when I had an option I choose for lightdm over kde.

Now I cant log in anymore my pc starts up and black screen. The only function thats working is alt ctrl f1 etc.


Greetings

---

### Post by sebastiaan5 on 2015-04-21
The command startx wont work getting several errors

---

### Post by flaymond on 2015-04-21
Try :

```
sudo service lightdm restart
```

---

### Post by sebastiaan5 on 2015-04-21
well I can log in again and surf the web etc, I needed to delete my nvidia driver completly, any tips to install Nvidia driver for GTX 860M

greetings

---

