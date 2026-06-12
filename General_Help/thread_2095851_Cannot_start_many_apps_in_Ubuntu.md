---
title: "Cannot start many apps in Ubuntu"
date: 2012-12-18
forum: General Help
---

### Post by daveysan on 2012-12-18
Hi.

I have a (Dell) laptop that I use occasionally (once a week or so). Today I find that some applications will not start from the unity launcher. When I click the relevant icon, they glow for a short while and then the glow ceases but the application does not appear. Applications that exhibit this behaviour include the terminal and display app. 

Odder still, when I start Netbeans (which does start from unity), the font in that app has changed to something fairly basic.

In order to troubleshoot, I started xterm (via alt-f2). From that I can start gnome-terminal as root but if I start as my normal user I get a Segmentation fault (core dumped) error (which probably explains why it won't work from the unity launcher).

Some apps along the top bar appear to have failed in the same way. I see my Dropbox icon but not the battery charger icon.

In researching this I found a possible problem installing gimp (I installed 2.8 last time I used the laptop), which seemed to introduce font issues. I have removed gimp completely (I think) but the problem remains. Creating a new user has not helped - I cannot even log in that way (after login I get the Ubuntu background with no icons at all).

Does anyone have any ideas? I have a fully updated x64 12.10 install.

Thanks ...

---

### Post by Arielxgbarton on 2012-12-18
If it would not be a huge amount of trouble, a complete reinstall would sort it out. Put all your files on a memory stick, make a DVD (yes not a cd) with ubuntu 12.10 on it (its larger than 700MB so will require a DVD) and write a list of all the softwaer you have, then reinstall. If that is not possible, tell me and I will try to look into what it is, unless someone else solves it for you

---

### Post by Arielxgbarton on 2012-12-18
If it is an old/slow laptop, and you wish reinstall to solve it, I would suggest that you install Lubuntu 12.10. If it does not work, saying that your CPU does not have the required features (it did for me) I would install Lubuntu 12.04

That is what happened to me. It said my processor did not have PAE, required to install it, so I installed the previous version

---

### Post by daveysan on 2012-12-18
It is an interesting one. The laptop is new and fairly powerful and the problem did not manifest itself until today (after trouble free use for the last couple of months). I can reinstall, of course, and will end up doing so if the current problem doesn't get resolved - but I'd prefer not to, partly from the hassle factor but mainly because it must be possible for the problem to happen again. I have used Ubuntu for a few years (and have it currently on 3 others computers) but have never seen this problem...

---

### Post by daveysan on 2012-12-20
Well, that is disappointing. Looking at /var/log/syslog I noticed that whenever I tred to open a terminal I got a segfault in libglib-2.0. Delving further, somebody suggested removing tweaktool (which I had installed and used without problems a couple of months ago). I did that and now the machine won't boot at all - it gets to the login screen but after entering my credentials I get the Ubuntu background and nothing else. Thus my trouble shooting will stop here and I shall reinstall. Thanks anyway to those that looked at the issue ...

---

