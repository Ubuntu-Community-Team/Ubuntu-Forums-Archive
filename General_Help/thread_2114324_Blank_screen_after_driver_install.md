---
title: "Blank screen after driver install"
date: 2013-02-09
forum: General Help
---

### Post by Mantinziza on 2013-02-09
Im currently running Ubuntu 12.04

I have an Nvidia Gtx 570. GC

When i first installed Ubuntu It ran just fine. I upgraded everything. And ran the driver install right through Ubuntu itself. There's only 3 driver options. All 3 of them result in the same problem. At the grub menu, I went into the system by pressing e, and i deleted quiet splash, and typed in nomodeset. Like I've been told to many times before.

Every time I do this 1 of 3 things happens, it takes me to a black screen that says login password. I tried typing my stuff into this field but it will NOT allow me to type anything. 

the 2nd, it says loading files. then it gets down to a a flashing type icon and stays like this. nothing else

the 3rd, it just stays a blank screen.

Since these are happening at random, im assuming that I'm possibly typing something wrong or putting a space in the wrong place.

I would much appreciate help with this, please be as accurate as possible

I am NEW to Ubuntu would really like it to use it, Please help.

---

### Post by Mantinziza on 2013-02-12
bump cause im still trying to find help

---

### Post by jim_deadlock on 2013-02-12
This kind of thing happens with my dad's Ubuntu installation every time there's a kernel update because he has an AMD graphics card which will only work with the proprietary driver, so I have to keep reinstalling it for him. So to me your problem sounds quite familiar and I think it's related to your video driver, although you have a nice common Nvidia card so it really shouldn't be happening.

Anyway, this may (or may not) help. People with more expertise than me may offer better suggestions but you can try this to be going on with.

When you get a black screen that says 'login' enter your username and you should get a password prompt. When you enter your password nothing will appear on the screen but it will accept it. Then you should have a normal shell prompt like you get in a terminal session (you are now logged in but without a graphical desktop). Enter this:

```
sudo apt-get dist-upgrade
```

It should ask for your password again, so type it invisibly again. This may or may not update a bunch of stuff, just wait till it finishes. Enter this:

```
sudo apt-get install nvidia-common
```

It may install or may say it's already the latest version or something else. Pay attention to what it says in any case, and post back here if necessary.

Finally:

```
sudo reboot
```

... and see what happens.

---

