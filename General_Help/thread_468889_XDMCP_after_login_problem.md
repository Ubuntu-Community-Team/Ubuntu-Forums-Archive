---
title: "XDMCP after login problem"
date: 2007-06-09
forum: General Help
---

### Post by SpaceClafouti on 2007-06-09
Hi anyone !
I'm brand new on **[COLOR="DimGray"]Ubuntu [/COLOR]**and i'm trying to get **XDMCP **working...
[LIST]
[*]I installed the latest Ubuntu distrib on a computer.
[*]I set up a static IP adress on it and configured a bit the overall programs running.
[*]Throught my network i'm getting in. (*I enabled **XDMCP **on [COLOR="DimGray"]**gdm **[/COLOR]via [COLOR="DimGray"]**gdm-setup**[/COLOR]*).
[*]I'm using [COLOR="DimGray"]**XMing **[/COLOR]on my remote computer.
[/LIST]
All seems to be fine: i can see the login screen and i can enter in. But !! The next screen is a kind of fadded-salmon (*it reminds me of an episod of Friend related with Ross and a faded-salmon shirt* :D) backgrounded screen with nothing ... :(
And if i try to get in on the machine itself using XDMCP, it's the same !!! Whereas if I login in a standard way, i can get in KDE (*or Whatever*).

As someone a clue to solve the problem ??

Thanks a lot anyway !
best regards.

---

### Post by Damanther on 2007-06-14
You might have already tried this. But its good to try the easy solutions first.

I got the same screen when I enabled XCDMP from the
System->Administration->Login Window menu.

It required a restart of the Xserver, (a plain old reboot works too) and all was well after that.

---

