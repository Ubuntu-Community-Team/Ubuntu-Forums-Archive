---
title: "Ubuntu upgrade broke my computer!"
date: 2015-09-08
forum: General Help
---

### Post by NotSoBrown on 2015-09-08
After ubuntu said it was no longer supporting updates i had to upgrade to the new one. I had been using plasma on kubuntu. now it has 2 sessions competing over each other. I have launched every type of ubuntu possible in the advanced boot options. Nothing is working. How am I going to fix this? here is a short clip of whats happening. [http://youtu.be/VaOhMlKfjwQ](http://youtu.be/VaOhMlKfjwQ) what do i do now? how do i fix this? there are VERY important files on here that I cant pull off. I'm at a loss here.

---

### Post by Yellow Pasque on 2015-09-08
[https://bugs.launchpad.net/ubuntu/+source/sddm/+bug/1446760](https://bugs.launchpad.net/ubuntu/+source/sddm/+bug/1446760)

---

### Post by NotSoBrown on 2015-09-08
> **Temüjin said:**
> [https://bugs.launchpad.net/ubuntu/+source/sddm/+bug/1446760](https://bugs.launchpad.net/ubuntu/+source/sddm/+bug/1446760)
so how do I fix it? can you explain it or make a list of steps?

---

### Post by Yellow Pasque on 2015-09-08
You run this in the terminal (assuming you're using Ubuntu 15.04 with systemd):
```
sudo systemctl disable sddm.service
```
Or just remove sddm entirely:
```
sudo apt-get purge sddm
```

---

### Post by ventrical on 2015-09-08
Kewl video. I need to ask question. What was the original install? Was it an ubuntu-desktop install and you installed kubuntu desktop on it? It looks like you have several desktops. You may be able to resolve this by going to terminal and try to :

```

sudo apt-get update

```

then

```

sudo apt-get dist-upgrade

```

It looks like you have the old lightdm and newer lightdm desktop managers competing for each other After you hit Ctrl+Alt+F1 and get to terminal , log in with your name and password and try those preliminary commands and then restart your lightdm session

```

sudo service lightdm restart

```

and get back to me..

Regards..

---

### Post by ventrical on 2015-09-08
> **Temüjin said:**
> You run this in the terminal (assuming you're using Ubuntu 15.04 with systemd):
```
sudo systemctl disable sddm.service
```
Or just remove sddm entirely:
```
sudo apt-get purge sddm
```

Guess we were typing at the same time :)

Regards..

---

### Post by Yellow Pasque on 2015-09-08
> **ventrical said:**
> Guess we were typing at the same time

It happens... 

Is that the new lightdm or sddm? I assumed the latter since it was blue and I saw that bug report (I'm a Debian user in case you're wondering).

---

### Post by ventrical on 2015-09-08
> **Temüjin said:**
> It happens... 

Is that the new lightdm or sddm? I assumed the latter since it was blue and I saw that bug report (I'm a Debian user in case you're wondering).

With kubuntu it is sddm but it looks like he originally loaded ubuntu-desktop so there would be lightdm on there (last I checked on upgraded ubuntu-desktop 15.10 it was lightdm). I have had this problem several time over years.. .loading kubuntu or xubuntu desktop on top of ubuntu-desktop (unity) never fails to have some sort of log on/greeter bug. I am always able to solve this by removing lightdm  and installing gdm. Perhaps he should try to remove lightdm since it is obvious that sddm and lightdm are conflicting (I assume).


Regards..

---

### Post by NotSoBrown on 2015-09-09
had kubuntu then upgraded through terminal. but it's fixed now thanks for all the help!!

---

