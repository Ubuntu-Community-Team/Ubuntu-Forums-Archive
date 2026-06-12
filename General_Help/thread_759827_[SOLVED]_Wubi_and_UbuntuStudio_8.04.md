---
title: "[SOLVED] Wubi and UbuntuStudio 8.04"
date: 2008-04-19
forum: General Help
---

### Post by supersound on 2008-04-19
Hi, will Wubi allow an install of Ubuntu Studio version of 8.04?

---

### Post by lfaraone on 2008-04-19
Just install the normal ubuntu system then do the metapackage.
```
sudo aptitude install ubuntustudio
```

or from synaptic.

---

### Post by supersound on 2008-04-19
Cool, thanks!

---

### Post by starcannon on 2008-06-14
[SIZE="4"]UPDATE[/SIZE]
The method that you need is found on this site:
[http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/](http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/)

the command if you want just that part is:
```

sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt

```

GL


Deleted old message, as I watch the Aptitude install going along I see the programs are getting installed as well. Thanks ffm

---

