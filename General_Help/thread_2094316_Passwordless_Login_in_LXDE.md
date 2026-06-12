---
title: "Passwordless Login in LXDE"
date: 2012-12-13
forum: General Help
---

### Post by omgomgwtfbbq on 2012-12-13
Hello!

I have what I think should be a simple question, but I've already spent several hours on Google and searching through help forums without much luck.

All I want is to be able to log in to open Ubuntu without having to use a password.  Now before anyone jumps down my throat about this (like I said, I've been reading forums all morning, so I'm already very familiar with the moralizing about passwords) let me explain my situation.

I run Ubuntu 12.04 in Oracle Virtualbox using the LXDE light desktop environment. To be more specific, I run 20+ simultaneous instances of this setup. The reason for this is that I'm running scientific applications that each need their own virtual environment.  It's a bit extreme, but it works and it gets the job done. However, when you're dealing with one or two linux boxes, that's one thing. When you're dealing with twenty, anything I can do to streamline the process helps.

The host OS is Windows 7 and the whole computer is heavily encrypted using Truecrypt. It is a self-contained system and no servers are involved.

Is there a way to make it so that I do not have to enter a password every time I power up one of these linux boxes (again, running LXDE as opposed to the normal desktop environment)? Moreover, is it possible to make it so that when I power up the linux box it will go straight to the desktop with no login screen at all?

It would really make me happy if that was possible. :)

Many thanks in advance for your help!

---

### Post by ibjsb4 on 2012-12-13
I believe what you are looking for is lightdm (lxde display manager) auto login.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=auto+login+lightdm&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=auto+login+lightdm&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Lars Noodén on 2012-12-13
The settings for that go in /etc/lightdm/lightdm.conf 
```

autologin-guest=false
autologin-user=omgomgwtfbbq
autologin-user-timeout=0

```

---

