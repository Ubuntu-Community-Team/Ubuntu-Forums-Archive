---
title: "kopete webcam with msn works just fine.."
date: 2008-07-01
forum: General Help
---

### Post by jaikat on 2008-07-01
hello guys..

i'm here to state that i'v successfully used my webcam on "kopete" here or my ubuntu gutsy, with a msn user on windows.

at first kopete recognized my cam, which is an acer orbicam built into my laptop. whenever i started sending the cam kopete crashed terminated. i googled for a solution, some people were saying there's something wrong with the "kdelibs4c2a" package and that there is a patch for it.

i fired up synaptic, and the package was already installed to the latest version. then i noticed "kdelibs" was not (i'm using gnome), so i thought "what the hell.." and installed it.

then i ran kopete again, used the "send webcam" button and the damn thing worked..

note: for those who use gnome and suffer from kopete crashes, try installing the "kdelibs" file from synaptic. it might just work. besides, its a very small file.

another note: kopete does support webcam with msn and maybe yahoo(only tried msn), but it doesn't have voice support for either one.

i still think this is great improvement.


ps: im running gutsy(7.10) on an acer aspire.


thanks
MJ

---

### Post by chronos00 on 2008-12-25
I would also like to report success in this matter, but after having connection problems. The problem is that Kopete does not support NAT for webcams, and must be configured manually.

My case, as many others, is that I use a router to share internet. In this situation, Kopete won't be automatically able to connect a webcam. As stated in the [COLOR="RoyalBlue"][KDE wiki]("http://wiki.kde.org/tiki-index.php?page=kopete%20webcam%20support")[/COLOR]:

> I can't receive any webcam stream from my buddies; what's wrong ?
MSN webcam support is not NAT-friendly. Check your NAT router and forward the MSN Webcam port to your computer port on which Kopete is listening for webcam (see Configure/Accounts/MSN/Connection).

The only thing you need to do to get the webcam working is configure the port forward at the router to your internal computer's IP; default port 6891.

Hope this helps someone!

---

