---
title: "Im writing this from windows... HELP! (video boot problem)"
date: 2008-06-06
forum: General Help
---

### Post by Ponomous on 2008-06-06
So i had to rma my graphics card the other day but figured i would be ok running the integrated graphics for a few days.  Boy was i wrong.  I reinstalled the drivers for the integrated graphics and what do you know but i get stuck in boot up on the gnome display checker (or something like that) it gets stuck in a loop for about 3 min and then i can type like im in the terminal but no commands work and its just a blank screen with white text that i type.  Looks kinda like dos.  I stole my friends graphics card and tested booting with it and it worked fine.  Windows, to my ultimate horror ,works fine with the integrated card.  Any ideas on a fix or should i just wait for my card to get back and suffer through xp...

---

### Post by PmDematagoda on 2008-06-06
What version of Ubuntu do you use? Also, boot Ubuntu in Recovery Mode and execute:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and then check if the GUI works properly with:-
```
sudo /etc/init.d/gdm start
```

---

### Post by Ponomous on 2008-06-06
Running 7.10, im at work right now so i will post the output when i get home.

Thanks

---

