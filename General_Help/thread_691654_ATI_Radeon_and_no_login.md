---
title: "ATI Radeon and no login"
date: 2008-02-08
forum: General Help
---

### Post by miket3115 on 2008-02-08
Hi 

I installed an ATI RADEON Sapphire HD 2400 in my comp today.  Now I am running a Dual boot with Ubuntu 7.1 and Windows XP.  Hope to be rid og the XP soon.  The problem I have come across is  when I booted into Ubuntu nothing works I get only a text prompt to log in no Desktop at all.  Looks like DOS.  What did I do wrong and How can I fix it?

Thanks

Mike

---

### Post by Rocket2DMn on 2008-02-08
Did it work before aka are you sure you installed the GUI stuff?  If so, then try running
```
sudo dpkg-reconfigure xserver-xorg -phigh
``` at the terminal.  Then run
```
startx
```

---

### Post by miket3115 on 2008-02-08
Thank you Rocket 2DMn,
 
It didn't even let me get close to installing anything, I simply shut down my comp installed the vid card and booted up. Went through the basic start up showing the Ubuntu logo then the colors went funny on the logo and it took me to a text login.  No idea what to do from there other than login.   I'm installing Ubuntu on an USB HD right now to see if it will will detect and integrate the vid card on install.

---

### Post by miket3115 on 2008-02-08
OK the install on the USB drive worked, I can login no problems.  So I know i did something wrong or there was something I was should have done when I installed the new vid card. Any thoughts?

---

### Post by Rocket2DMn on 2008-02-08
It's possible you forgot to tell it to install the GUI (sometimes people do this), or it just didn't detect your video card correctly.  Do you want to troubleshoot your first install?  Since it worked on the USB drive, it might be easier to reinstall on the hard drive since you don't have anything on there to lose yet.

---

### Post by miket3115 on 2008-02-09
That is what I've done thanks for the help anyway.

---

