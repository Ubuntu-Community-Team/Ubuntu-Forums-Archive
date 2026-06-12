---
title: "Cannot wake up my laptop after sleep:"
date: 2014-07-25
forum: General Help
---

### Post by radibg2 on 2014-07-25
When i close my laptop screen it not goes sleep, only turns off the screen, when i open it the screen is black and i can't do anything except to turn it off and on by the power button. When it is on battery and is not used for some time it sleeps, but when i login it stay black screen and again i can't do anything. How to fix this problem? Here are shots from my Light Locker Settings and Power Manager:[https://copy.com/FObcMgo4o3aM](https://copy.com/FObcMgo4o3aM)

---

### Post by tgalati4 on 2014-07-25
Let's try a couple of things.  Close any open applications--you don't want to lose any work while doing this.  Close the lid, wait a few seconds, then open it again to a black screen.  Try to get to a terminal with Control-Alt-F1.  If you see a command prompt to login, then log into your account and shutdown from the command line:

```
sudo shutdown -h now
```

Then try it again, but instead of logging in, hit Control-Alt-F8 to see if your graphical desktop returns.  If so, then see if everything works correctly.  If not, then Control-Alt-F1 to get back to a terminal, log in, then shutdown.

The make and model of your computer would be helpful and the version of Xubuntu you are running.

---

### Post by Bucky Ball on 2014-07-25
Are you using Lightlocker to set the suspend?

---

