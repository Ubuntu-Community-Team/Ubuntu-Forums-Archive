---
title: "Duel Monitors used to work, now not so much."
date: 2008-06-23
forum: General Help
---

### Post by rossjman1 on 2008-06-23
Hi. I have a dual monitor setup that was working a few days ago. Then I installed SimCity 4 and ran it with wine. The game went into full screen, my second monitor went from extending my desktop to displaying the exact same thing as my primary monitor. To change it back I have to go into ATI Catalyst Control Center > Display Manager and change my display mode from "clone desktop" to "Big Desktop". Then a message pops up saying I have to restart my system for the changes to take effect, but when I restart the second monitor is still displaying the same thing as my primary. Does anyone know how to fix this?

---

### Post by rossjman1 on 2008-06-24
Please help!
```
jeff@jeff-laptop:~$ aticonfig --dtop=horizontal
Warning: Option 'DesktopSetup' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.
jeff@jeff-laptop:~$ 

```
Ok. sudo aticonfig didn't give me any errors, but dual monitors are still not working. I don't understand why running a game in wine causes the seemingly unfixable problem.
Also, I know that dual monitors will work, because I had this setup running for a week before I tried to install SC4. Dual monitors still works in GDM, but as soon as I log in it 'clones' my primary.
ATI Mobility Radeon X1400 is my graphics card.

---

### Post by rossjman1 on 2008-06-25
...

---

### Post by rossjman1 on 2008-06-28
Doesn't anyone know any type of fix?

---

### Post by Nemo8 on 2008-07-14
Well i am a beginner in ubuntu and for me you got lucky to have been able to configure 2 monitors.I have a ati radeon 9550 and my 2 monitors show the same image

---

### Post by tramir on 2008-07-14
Does it help if you do this?
```
sudo aticonfig --initial --dtop=horizontal
```

---

### Post by rossjman1 on 2008-07-15
no it says that it doesnt affect the current session.

---

