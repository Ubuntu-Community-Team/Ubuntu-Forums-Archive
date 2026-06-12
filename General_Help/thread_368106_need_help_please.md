---
title: "need help please"
date: 2007-02-22
forum: General Help
---

### Post by don3390 on 2007-02-22
I have version 6.06.1 LTS  can some one please show me how to connect to the internet?
I have the  Official Ubuntu Book. It can't be this hard I know just can't get it . Love what I see in ubuntu.

---

### Post by Hishgraphics on 2007-02-22
If you have an Ethernet LAN connection with a broadband account run:

```
sudo pppoeconf
```

hit yes all the way, and enter your login and password to your account when asked to.

```
pon dsl-provider
```
... when you want to reconect later

```
plog
```
... to check your connection status

---

### Post by don3390 on 2007-02-23
Sorry was not thinking, so didn't give all the specs. I have a dial up modem, to far out in sticks for broad band

---

### Post by reclusivemonkey on 2007-02-23
Do you have an external modem, or an internal modem. Internal modems are poorly supported in Linux. Getting an external modem will make your job considerably easier.

---

### Post by don3390 on 2007-03-03
I'm back. I have an external modem TFM-560X which is suppost to  suport Linux. I have a dial up. My real problem is not knowing how to set up even though I've looked at the book.
I can set up  using XP Home no problem. Don't know where to put the phone number at. I'd really love to get on the internet using ubuntu. I think I need a book on Linux for stupid and work  my way up to linux or dummies

---

### Post by stupidlongname on 2007-03-03
System - Administration - Networking.

You'll find the modem setup there

---

### Post by don3390 on 2007-03-05
Thanks for all your help. I can not connect to the internet, the modem works. I've made it this far thanks to your advice. I now have to read some other  post and see why when i try to get firefox it tell me it can't find it or any other web site I try, but I did aleast get the connection to internet. Thanks again

---

