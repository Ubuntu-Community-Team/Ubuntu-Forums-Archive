---
title: "Ubuntu wont start up"
date: 2007-03-05
forum: General Help
---

### Post by Harriscat on 2007-03-05
Hello Everybody,

I have recentley installed edgy eft onto my system it was working fine until I decided to restart my system, When the ubuntu loading screen came up the status bar loaded and then went to a solid black screen and would refuse to start up?

I am using a compaq with one gig of ram and Amd Turion64 x2 using an nvidia graphics card.


Cheers guys

Charlie

---

### Post by ripntime on 2007-03-05
Well most times i come across this it's video related so what you should do is from the shell, if you don't see it then [ctrl+alt+F3] login.
run [sudo dpkg-reconfigure -phigh xserver-xorg].
it should detect/fix things and get you going again.
If that don't do it all little more info would help.
any apt-get update recently etc ?

---

### Post by ripntime on 2007-03-05
Oh and what nvidia drivers were you using, xorgs [nv] the open [nvidia] or proprietary [nvidia]? and any kernel changes lately [since last reboot].?

---

### Post by Harriscat on 2007-03-05
When I try to login using crtl alt f3 the login shows up for about 2 secounds and then disapears?

Charlie

---

