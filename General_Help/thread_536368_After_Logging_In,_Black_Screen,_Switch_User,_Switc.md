---
title: "After Logging In, Black Screen, Switch User, Switch Back, It's There! WTF?"
date: 2007-08-27
forum: General Help
---

### Post by vbgunz on 2007-08-27
I have this problem I didn't think too much of because I personally never experience it when logging into my account (usually I always log in first after bootup). I see this when I switch to my sons account. I log him in and the screen goes black. You can hear the welcome music but nothing happens on screen (at least I cannot see it). If I switch back to my account (usually Ctrl+Alt+F6) and then switch back (usually Ctrl+Alt+F9), the screen is there.

At first this was a minor annoyance but on either system, launching OpenGL games e.g., Planet Penguin Racer, Neverballs, etc, results in the screen going and staying black. Again, it appears the only fix is to switch to another screen (Ctrl+Alt+(F1 through F9)) and switch back. From a minor annoyance, it is now a big and bad one. Anyone know why the first account (my account) does not go black after logging in but my sons does? Anyone know why both accounts go black after launching an OpenGL game?

I would really appreciate any feedback on this. I am using Kubuntu 7.04, Nvidia binary driver 100.14.11 and everything else seems to be just fine. I upgraded to the latest binary driver found on the official nvidia site because of this problem I had [http://ubuntuforums.org/showthread.php?t=525559](http://ubuntuforums.org/showthread.php?t=525559)

Any help is sincerely appreciated, thank you!

---

### Post by ddrichardson on 2007-08-27
I reported this as a bug in fiesty with user switching a while ago but don't appear to have had any feedback.

---

### Post by vbgunz on 2007-08-27
dd,

this only happens on either the second login (my sons account) OR when either account launches an OpenGL game. The only way to fix both situations is to switch to another user or screen and then switch back. If this is exactly your problem, can you please link me to your bug report so I can confirm it?

Thank you!

---

### Post by ddrichardson on 2007-08-27
OK, no its different. Mine only happens when I try to switch users.

---

### Post by vbgunz on 2007-08-31
The other day, I decided to clean up my system as much as possible. I ran through all dirs looking for leftovers (uninstalled programs, leaving junk behind) and deleted as much as I could (shocking how much garbage can pile up) I ran kleansweep 0.2.8 on Kubuntu 7.04, fully updated and now the blank screen problem is gone.

If you're looking for an answer to this I cannot say for sure that kleansweep did the trick (it could have been the update or my manual cleaning). anyhow for those with similiar problems, if you come across this thread, just be aware kleansweep albeit powerful can be very dangerous. be careful. good night and good luck :)

---

