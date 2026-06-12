---
title: "Desktop wallpaper and nothing else after update"
date: 2015-03-01
forum: General Help
---

### Post by PopsTheSailor on 2015-03-01
I get my desktop background image but nothing else. I tried a couple of old kernels and they didn't work either. If I go into recovery mode and then select resume my UI comes back. The other difference, probably, is that I'm running MATE and not Unity.

In Recovery mode, I also tried the option to fix broken packages and got an error when it tried to rresolve to a URL. It then said to try apt-get update with --fix - missing or something like that but it didn't give the exact command to try.

---

### Post by PopsTheSailor on 2015-03-01
Update: I ran the 4 commends above and tried again. With MATE it still had the same issue. If I selected to log in with Unity, my UI came back up. Anyone have any ideas on how to fix MATE? Or how to revert back to before the last upgrade? As I mentioned I tried a few of my old kernels and that didn't work Or how to reinstall Ubuntu over the top of my current config but NOT change my installed programs or other set up?

---

### Post by Bucky Ball on 2015-03-01
***Posts moved to own thread.***

... as your problem appears unrelated to the original poster's on the other thread.

The commands you ran were:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Which release are you using and how did you upgrade? You upgraded to a newer release, or did a regular update/upgrade?

---

### Post by PopsTheSailor on 2015-03-01
I'm using 14.04 (with MATE UI). It was a regular update that automatically pops up when I'm using Ubuntu through Update Manager.

---

### Post by Bucky Ball on 2015-03-06
You could try choosing Unity (Ubuntu session?) from the Sessions menu at login. Click the Ubuntu symbol in the top right of the GUI where you put your password (NOT 'Guest Session').

If you could at least get to a functional desktop it will give you a better chance of researching what happened with Mate.

---

### Post by PopsTheSailor on 2015-03-06
Yes, that is exactly what I have done. I'm on Unity right now searching for clues /  answers.

---

