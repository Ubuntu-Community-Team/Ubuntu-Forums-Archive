---
title: "Missing login screen"
date: 2007-12-28
forum: General Help
---

### Post by brad1138 on 2007-12-28
In Gutsy, If I log in, then "switch user" and log into another user, then log out, instead of the standard login screen I have a blank screen, slightly brighter than the normal login screen with nothing on it. I can login I just cant see what I am typing. Any Ideas?

Thanks,
Brad

---

### Post by taurus on 2007-12-28
What happens if you restart X with <Ctrl><Alt>Backspace from the GUI login screen?  Would that bring back the GUI login screen again?

---

### Post by brad1138 on 2007-12-28
> **taurus said:**
> What happens if you restart X with <Ctrl><Alt>Backspace from the GUI login screen?  Would that bring back the GUI login screen again?


Ya that brought the login screen back. It flashed the background from the first user I switched out of, then went blank for a sec then the login screen.

Brad

---

### Post by SanskritFritz on 2007-12-29
I also have the same problem. Ctrl-Alt-Backspace is not a good solution, as it nukes my session I want to switch to. Any more ideas? As said before by **brad1138**, we can login by typing the password on the blank screen, but it just jooks ugly. Maybe worth mentioning, I have wide screen (1440x900) and Nvidia GeForce 7300 GS with the proprietary driver.

---

### Post by brad1138 on 2007-12-29
> **SanskritFritz said:**
> Maybe worth mentioning, I have wide screen (1440x900) and Nvidia GeForce 7300 GS with the proprietary driver.

I also Have wide screen (1680x1050) and Nvidia GeForce 7600 GS with the proprietary driver. If that could have anything to do with it. 

I did do this "fix" for slow boots after login [http://ubuntuforums.org/showpost.php?p=3878110&postcount=32](http://ubuntuforums.org/showpost.php?p=3878110&postcount=32)  discussed on this forum.

Brad

---

### Post by SanskritFritz on 2007-12-30
I didnt apply that fix, I dont have that problem. Maybe we should try the open source driver for nvidia?

---

### Post by brad1138 on 2007-12-30
> **SanskritFritz said:**
> I didnt apply that fix, I dont have that problem. Maybe we should try the open source driver for nvidia?

Ya, I think I had the prob before I tried that fix. I would rather deal with the prob then use the non-Nvidia driver. But we could try it to see if it makes a difference. Hopefully we will see some more ideas here before too long.

Brad

---

### Post by Maelvon on 2007-12-31
I've the blank screen, when I switch users, and one users is already connected. 

If the users "disconnect" themself, instead of switching, it does not appears.

I've a Nvidia drivers, and the visual effect are set to "best". So the blank screen does not appears if I set the special effects to "normal" when I switch users.

That's all, I've not find a solution, only setting the desktop  special effects to "normal".

Ubuntu 7.10 - Gutsy Gibbon - Nvidia GeForce 6150

Maelvon

---

### Post by SanskritFritz on 2008-01-03
Anyone has tried the OSS nVidia driver? I will if time permits, but I'm a little afraid of the consequences...

---

### Post by Sukarn on 2008-01-03
This question was asked in another thread. MY suggested solution is to switch to a terminal (Ctrl+Alt+F1) and then switch back to the login screen by Ctrl+Fx where x can be anything between 7 and 12 by default.

---

### Post by SanskritFritz on 2008-01-05
> **Sukarn said:**
> This question was asked in another thread. MY suggested solution is to switch to a terminal (Ctrl+Alt+F1) and then switch back to the login screen by Ctrl+Fx where x can be anything between 7 and 12 by default.That didn't help here :-(

---

### Post by SanskritFritz on 2008-01-14
I plan to switch to the free nVidia driver. Should I expect problems? Can anyone point me to a thread here about the free and proprietary nvidia drivers?

---

