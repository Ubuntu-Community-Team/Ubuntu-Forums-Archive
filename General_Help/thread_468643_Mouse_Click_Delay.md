---
title: "Mouse Click Delay"
date: 2007-06-09
forum: General Help
---

### Post by volcodc on 2007-06-09
Hello, Im using Feisty Fawn 7.0.4 version of Ubuntu.


I just installed it as of this morning and having a great time with it, theres only 1 problem that is really bothering me.

I play quake 3 arena all the time, and with ubuntu, i seem to be getting this 1 second click delay with my mouse, so when i click fire, it takes a second or two to fire. No im not new at the game and I ping 20 to the servers i checked on, its not lag. 

Anyone know a solution or maybe whats wrong?
Thanks.

---

### Post by LollYouSuckZor on 2007-06-09
All I can think of is Lag. :)

---

### Post by volcodc on 2007-06-09
no, not lag, i have done many tests and its not the lag that is causing the delay :(

---

### Post by volcodc on 2007-06-09
After searching for awhile i found the fix:

Open up Xorg.conf and change emulate3mouse to false.
then reboot

now i have no delay, sweet.

---

