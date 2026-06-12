---
title: "Hardy can't login to xfce/gnome after boot."
date: 2008-06-08
forum: General Help
---

### Post by tristan on 2008-06-08
Hi all. I recently upgraded (via fresh install) from Gutsy to Hardy and for the most part it's really excellent. I installed the xfce metapackage as I prefer to use xfce for general usage, whilst being able to drop into a pimped out gnome to impress others....

The problem is: after booting the computer, the first time that I go to login to xfce via gdm, the screen clears but nothing else happens. The system is not frozen, so I can ctrl-alt-backspace to restart x and back to gdm. If I then login again, xfce starts up normally and can be logged out/logged in without problems. As soon as the computer is rebooted though, the problem reappears. 

I've set up several users and the problem occurs with them too. It also occurs logging in to gnome.

I can't see anything in dmesg or in .xsession-errors which gives me a clue to what is going on. I've reinstalled gdm, and tried changing gdm themes. Nothing helps.

Any ideas?

---

### Post by Bubba64 on 2008-06-08
> **tristan said:**
> Hi all. I recently upgraded (via fresh install) from Gutsy to Hardy and for the most part it's really excellent. I installed the xfce metapackage as I prefer to use xfce for general usage, whilst being able to drop into a pimped out gnome to impress others....

The problem is: after booting the computer, the first time that I go to login to xfce via gdm, the screen clears but nothing else happens. The system is not frozen, so I can ctrl-alt-backspace to restart x and back to gdm. If I then login again, xfce starts up normally and can be logged out/logged in without problems. As soon as the computer is rebooted though, the problem reappears. 

I've set up several users and the problem occurs with them too. It also occurs logging in to gnome.

I can't see anything in dmesg or in .xsession-errors which gives me a clue to what is going on. I've reinstalled gdm, and tried changing gdm themes. Nothing helps.

Any ideas?

I sometimes have the same problem I haven't really looked for an answer to this, but I have found that if you wait around 30 seconds after dropping the desktop ubuntu to login to get to xubuntu it seems to log in with no blank screen.

---

### Post by krivine on 2008-11-05
I upgraded from Gutsy to Hardy yesterday, on an old laptop, and found the same problem.

It seems to have gone away now I've set the 'Simple' splash screen (Applications > Settings > Settings Manager > Splash Screen). I don't know if this is significant, or just one of those things, but this splash screen does report what it's doing, so if it fails in the future I should have an idea of where the failure is. 

I don't like splash screens, but if using one saves me having to log in twice, well...

---

