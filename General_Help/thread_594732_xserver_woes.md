---
title: "xserver woes"
date: 2007-10-28
forum: General Help
---

### Post by dean20007 on 2007-10-28
Okay folks I have been an idiot. After upgrading to gutsy I noticed that it seemed very slow to interact with windows. So I thought "No problem it will be video drivers". So I played about with the ATI Radeon dirvers to see if I could get the 1280*1024 that I had with feisty. After this didn't work I thought I would reconfigure the xserver. I went through the options accepting the defaults (it auto detected it as ATI Radeon 5500) which is correct. However on reboot everything seems fine until the login screen when I can see the screen however it appears extremely blue and hard to make out. I am completely stumped now.

Am I doomed? Can Anyone help?

---

### Post by ceno-byte on 2007-10-28
Hello deam20007 maybe you can try reconfiguring x try this from a terminal 

```
sudo dpkg-reconfigure x-server-xorg
```

Also when you make it to the login screen if the above solution doesn't work try logging into ubuntu with fail-safe gnome from the sessions menu.

---

