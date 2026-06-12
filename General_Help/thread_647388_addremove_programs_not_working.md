---
title: "add/remove programs not working"
date: 2007-12-22
forum: General Help
---

### Post by spamburger on 2007-12-22
When I go to add/remove programs and check a program for install, it says I need a working internet connection and to reload. So I hit refresh and it does the same thing. I know I have a working internet connection, because well, I'm posting this right now from Ubuntu. Any help?

---

### Post by andrewcmcardle on 2007-12-22
you may want to try the synaptic package manager, look in the menu

---

### Post by TidusBlade on 2007-12-22
I think I got it once, and I ignored it and continued normally...

---

### Post by forestpixie on 2007-12-22
if you didn't have a working connection when you installed/upgraded I think you might find all the repos are commented out in your sources.list

if you don't know - post it here, do this in a terminal and paste your sources here

```
cat /etc/apt/sources.list
```

---

### Post by spittal on 2007-12-23
I had exactly that problem and the cause is as described. Installed without working internet connection. I solved the problem by running
*sudo gedit /etc/apt/sources.list*
I found that each of the lines which had been commented out were preceded by a message saying that this had been done. I deleted the warning lines and the comment # from each of the other lines saved the file and that was it fixed. Thanks so much for the info. I am now a happy guitarist:guitar:

---

