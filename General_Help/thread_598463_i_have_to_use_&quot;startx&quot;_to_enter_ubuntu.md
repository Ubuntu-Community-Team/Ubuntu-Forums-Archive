---
title: "i have to use &quot;startx&quot; to enter ubuntu"
date: 2007-10-31
forum: General Help
---

### Post by charles_316 on 2007-10-31
after having some problems installing ubuntu with that blue display screen error, i followed some guides online and edited some config files i believe...

well now i have to enter ubuntu by doing "startx" at the terminal... it doesn't go into a splash screen and then into ubuntu

i think the tutorial had asked me to disable or remove the splash screen plus gui or something?

How do i revert it back so that it can just start up into ubuntu instead of starting to terminal?

---

### Post by aysiu on 2007-10-31
Try entering this at the terminal instead of *startx*: ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
```

---

### Post by charles_316 on 2007-10-31
thanks.. i will try that

yes i think it was called gdm that i had to disable

what is gdm? the gui

---

### Post by aysiu on 2007-10-31
It stands for *Gnome Display Manager*, but it's basically the login screen.

---

### Post by charles_316 on 2007-10-31
interesting...

i tried it run the recovery mode terminal.... and init.d directory did not exist... so i tried running gdm restart from /etc/ and it worked... it went to a unique login screen that i have not seen before and continued into ubuntu... however, when entering ubuntu from recovery mode... for some reason it freezes after i try to logout... (hitting the button in top right)..

now trying from normal mode... the command:

sudo apt-get install ubuntu-desktop

did not do anything... w/ the recovery mode terminal, it actually had a response and said ubuntu was at its latest version.... 
also for normal mode there was no init.d directory so i tried gdm restart anyways and it gave me this:

gdm[5683]: WARNING: GDM file gdm-daemon-config.c: line 2121(): Cannot run seteuid to 0: operation not permitted

so it did not work in normal mode for some reason?

any ideas?

---

### Post by charles_316 on 2007-10-31
anyone know how to restart gdm?

---

### Post by kavithas on 2008-04-25
> **aysiu said:**
> Try entering this at the terminal instead of *startx*: ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
```
[SIZE=2]
[/SIZE] [SIZE=2]The solution worked for me beautifully, though my problem scenario was slightly different. I was in a situation wherein after upgrading to 8.04, none of the GNOME panel buttons worked and I could not launch any application(including the terminal). I followed the above instructions and now everything seems to be fine. Thank you![/SIZE]

---

