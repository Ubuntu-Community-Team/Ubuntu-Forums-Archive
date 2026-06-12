---
title: "Install Gnome after installing 6.06 LAMP server"
date: 2006-12-18
forum: General Help
---

### Post by geuis on 2006-12-18
Hey folks, I'm surely to get fire from more advanced admins, but I need to ask anyway.

I am setting up an old machine here at the office w/ the Ubuntu 6.06 LAMP server options. The install went perfectly.

My question is, I would also like to put Gnome in here as well, for use when I am just working with the machine.

Is there an easy way to do this, like "sudo apt-get install ubuntu desktop" or something?

---

### Post by taurus on 2006-12-18
Yip...

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by geuis on 2006-12-18
thanks taurus. I remembered how after a few minutes :)

---

