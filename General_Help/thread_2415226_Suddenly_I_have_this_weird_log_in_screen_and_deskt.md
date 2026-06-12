---
title: "Suddenly I have this weird log in screen and desktop environment"
date: 2019-03-22
forum: General Help
---

### Post by confused322 on 2019-03-22
Hi!

I have Ubuntu 18.04 installed. I also installed the xubuntu desktop environment. Everything was working well untill I booted my laptop this evening and the login screen was completely changed. I can't select which environment to use. I have to enter my username and then the password. When I am logged in it sorta looks like Unity but is also weird (for example I can not log out, my scroll settings has been inverted/reset etc, Firefox settings changed). This is utterly frustrating.

I took a photo of the log in screen: [https://i.postimg.cc/tRWcVYdJ/login.jpg](https://i.postimg.cc/tRWcVYdJ/login.jpg)

Does anyone know what has happened and in what direction I need to look to get it fixed? I have no idea where to look now or what to search.

Thanks!

---

### Post by confused322 on 2019-03-22
Oh I got it. I accidentally configured a different display manager (xdm I think). 

Reconfigured it with: 

sudo dpkg-reconfigure lightdm

---

### Post by ajgreeny on 2019-03-22
Great news! 
Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

