---
title: "ATI logout-login screen resolution issue"
date: 2007-05-17
forum: General Help
---

### Post by prospectofdeath on 2007-05-17
I realize similar threads to this have been started before and some of them even have solutions but I think this problem is a little different.

I've got a Benq FP202W and ATI Radeon X800PRO running on a Feisty box with the latest patches. The screen is set at 1680x1050 resolution and there are two valid user accounts.

During installation it detected both my video card and monitor. The default resolution for this card/monitor appears to be 1680x1050.

When I first bring the machine up in Feisty I'm presented with a perfectly rendered login screen. I don't know what the resolution of that screen is but it looks close to 1680x1050. I log in using my normal user account and I'm presented with a desktop that's 1680x1050.

If after logging in successfully I decide to log out, instead of getting the login screen, I get an "Out Of Range" error from my monitor. I assume this is because the login screen is changing it's resolution to something higher than my monitor can handle.

I've created a second account for testing some software. When I log back and forth between these account I have to reboot the machine otherwise I don't get a login screen.

Is there a solution for this? Is there a place where I can manually set the login screen resolution? Is this a bug with the monitor somehow? Is this just a cruel twist of fate?

When I initially log in everything is fine. The problem _only_ occurs when I log out. If I reboot everything is back to normal. Thoughts?

---

### Post by Kent84 on 2007-05-19
I experience the same problem with a ATI Radeon 9600pro after installing the ati drivers following the instructions on: [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2674273](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2674273)

---

