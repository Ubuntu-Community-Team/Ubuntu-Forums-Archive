---
title: "Can't get Google Earth to run"
date: 2007-08-10
forum: General Help
---

### Post by 9a3eedi on 2007-08-10
ok, I admit I am not using Ubuntu at the moment (Gentoo here), but I had the same problem in Ubuntu. I installed Google Earth from the repositories, both when I used Ubuntu and right now when I am using Gentoo. It installes fine, but when I run it, the splash screen appears, and then it simply stops there. No loading, no nothing. Starting it from the command line gives no message. 

I used to run amd64 ubuntu on this PC, and am now running amd64 Gentoo on this PC, and still have the same problem.

Anyone?


EDIT: I just realized that google earth seems to use up one of my CPU cores while it is sitting there with its splash screeen idle

---

### Post by swisscow on 2007-08-10
Could be a video card issue. I have an ATI x300 and googleearth only works with the fglrx drivers - otherwise I get the same hung screen like you.

There is a trick which MAY work, you start googleearth from a command line with something like display:=0 googleearth. THIS IS PROBABLY NOT THE EXACT COMMAND, but I've just got back from holiday and I can't remember what it is and I'm too tired to find it - sorry.

---

### Post by amarra on 2007-08-21
I've found the following workaround for ATI cards with fglrx:

[http://wiki.sabayonlinux.org/index.php?title=HOWTO:_Google_Earth_freezes_at_splash_screen](http://wiki.sabayonlinux.org/index.php?title=HOWTO:_Google_Earth_freezes_at_splash_screen)

It works for me.

Bye 
Antonio

---

