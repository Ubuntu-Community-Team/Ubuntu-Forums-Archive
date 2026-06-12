---
title: "how to make a new DE the default environment"
date: 2015-11-17
forum: General Help
---

### Post by matt18 on 2015-11-17
I am installing ubuntu 14 lts onto a older machine. The machine has 2GB ddr400 ram with a new 320GB sata 3 HDD and a AMD CPU roughly 2500+ maybe higher. It can run win 2000 and xp with no issues.

However, this machine is for my dad and unity is not so fast with this machine. So i want to install LXDE. i will be using the following command

sudo apt-get install lubuntu-desktop

this will hopefully install what i need. But then i want that to be the default DE when my dad logs in.

thanks

---

### Post by deadflowr on 2015-11-17
Aside from the fact that you should install the lubuntu desktop directly from a lubuntu installation media : [https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

If you really need to do this it from an install of ubuntu, then all you need to do is set it as the selection in the login screen.
In Ubuntu's login screen there will be an icon in the top right corner of the box that has the users username and password field.
simply click on that box and you can select the lubuntu session. Then login.
This persists forever for each users setup.

---

### Post by matt18 on 2015-11-17
i do not want the lubuntu OS because it does not have what i need by default and i dont want to have to spend alot of time downloading all the stuff i need. . I want what is installed by default with ubuntu but with the LXDE desktop:)

EDIT.

I think i might have misunderstood your reply.. im not sure i get what you are meaning

thanks

---

### Post by flocculant on 2015-11-17
>  I think i might have misunderstood your reply.. im not sure i get what you are meaningdeadflowr's reply stems from your post where you say you're going to install lubuntu desktop, that's all of Lubuntu

you really want to be looking at installing lxde

```
   sudo apt-get install lxde
```

That though still appears to grab a bunch of apps. You could try with --no-install-recommends to cut those down a bit.

---

