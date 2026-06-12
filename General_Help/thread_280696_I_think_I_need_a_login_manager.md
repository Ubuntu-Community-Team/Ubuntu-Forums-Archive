---
title: "I think I need a login manager?"
date: 2006-10-19
forum: General Help
---

### Post by paul6 on 2006-10-19
I did a server install of Dapper, and got Openbox as my windows manager. When I boot up my computer, I have to login with my name and password and than type "startx" to get in Openbox. My question is, is there a program that will automate this for me?

---

### Post by kerry_s on 2006-10-19
yes you can use xdm,wdm,gdm,kdm just like a regular install. I prefer to use gdm for all WM's and gnome and kdm for kde.

sudo apt-get install gdm

make sure you select openbox in the session menu. Then when you login you can setup the auto login option.

---

### Post by taurus on 2006-10-19
And don't forget to run

```
sudo /etc/init.d/gdm start
```

---

