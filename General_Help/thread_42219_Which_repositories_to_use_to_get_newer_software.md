---
title: "Which repositories to use to get newer software"
date: 2005-06-16
forum: General Help
---

### Post by mbourd25 on 2005-06-16
Hi, I want to be able to install the latest software but the repositories that I'm using, from [www.ubuntuguide.org](www.ubuntuguide.org), gives me older software versions. Which repositories should I use to get the latest software releases?

For example, for the Nvidia video drivers, in those repositories, it has version 71 but on the Nvidia website they are up to version 76.

Any help would be great.

Thanks.

---

### Post by christooss on 2005-06-16
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted

Maybe those drivers hasnt been backported

---

### Post by mbourd25 on 2005-06-16
Hi christooss, thanks for your fast reply.

Do I had these lines and leave the others their or do I delete any of the lines in my source.list?

Thanks.

---

### Post by christooss on 2005-06-16
[QUOTE=mbourd25]Hi christooss, thanks for your fast reply.

Do I had these lines and leave the others their or do I delete any of the lines in my source.list?

Thanks.[/QUOTE]
 You should have only this lines in suorces.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted

---

### Post by mbourd25 on 2005-06-16
Excellent, that's want I wanted to know. So I'll get rid of the other ones and use the ones you provided to me for my source.list.

Thanks for your help. Man this forum rocks.

---

### Post by mbourd25 on 2005-06-27
Hi Folks, I want to try Kubuntu out and I've been seeing some comments where they say use the same repositories from Ubuntu with Kubuntu. Is this true?

If no, which repositories should I use for Kubuntu?

Thanks again.

---

### Post by rpgcyco on 2005-06-27
Yep, it uses the same repositories as normal Ubuntu. Just run:

```
sudo apt-get install kubuntu-desktop
```

to install it. :)

- Rpg Cyco

---

