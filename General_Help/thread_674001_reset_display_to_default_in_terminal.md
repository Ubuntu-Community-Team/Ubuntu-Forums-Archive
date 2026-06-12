---
title: "reset display to default in terminal?"
date: 2008-01-21
forum: General Help
---

### Post by pspfreak101 on 2008-01-21
I recently got a new gfx card and I changed the settings so that it would diaply alittle better anyways when I restarted it would just go to the boot screen then the screen would flash 5 or 6 times till you get a blue screen thta says somethings wrong and in 2 minutes it will try on diaply 0 anyways I have 2 minutes in the terminal before it happens all over again so can some please tell me how to reset the display in the terminal

---

### Post by csulok on 2008-01-21
you should boot your linux into safe mode, using the grub menu and selecting the safe mode option - the second from the top usually.

there you get a command line interface with root logged in. type the following there:

```
sudo dpkg-reconfigure xserver-xorg
```

this will guide you through keyboard mouse and display settings. when done reboot by hitting ctrl+alt+del

---

### Post by jfj1723 on 2008-04-09
Just wanted to say thanks! I set up an ASUS EeePC with xubuntu and set the wrong resolution... that little screen cant seem to do 1200x900... ooops... But your fix did the trick! Thanks!

---

