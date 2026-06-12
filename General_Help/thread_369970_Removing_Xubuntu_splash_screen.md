---
title: "Removing Xubuntu splash screen"
date: 2007-02-25
forum: General Help
---

### Post by geovino on 2007-02-25
I install the Xubuntu desktop and it's fine but how do I get the regular Ubuntu opening splash screen to come up at the beginning instead of the Xubuntu opening screen? 

I just wanted to see how Xfce works here but I still like Gnome better.

---

### Post by solar george on 2007-02-25
Run the command

```
sudo apt-get remove usplash-theme-ubuntu
sudo apt-get install usplash-theme-ubuntu
```

---

### Post by geovino on 2007-02-25
Thank you.

I see that I still have Xfce installed so I can use it if I want to, or I can unistall it with out effecting Gnome or anything else?

---

### Post by solar george on 2007-02-25
Try this,

```
sudo apt-get remove xubuntu-desktop
sudo apt-get install ubuntu-destop
sudo apt-get autoremove
```

the second step may say that it is already installed, just move on to the next step.

---

### Post by geovino on 2007-02-25
Ubuntu-desktop wasn't installed. I installed it via Synaptic. Why wasn't that installed when I installed Ubuntu initially? Or was it uninstalled when I installed Xubuntu-desktop?

---

### Post by solar george on 2007-02-25
Ubuntu-desktop was removed when you installed xubuntu-desktop

---

### Post by Kateikyoushi on 2007-02-25
Why ? I also installed xubuntu-desktop on ubuntu and still have both. Why was it removed in his case ?

---

