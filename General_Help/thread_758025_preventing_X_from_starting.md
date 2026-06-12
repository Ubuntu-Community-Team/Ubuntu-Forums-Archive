---
title: "preventing X from starting"
date: 2008-04-17
forum: General Help
---

### Post by happypig on 2008-04-17
following this post :

 [http://ubuntuforums.org/showthread.php?t=743477](http://ubuntuforums.org/showthread.php?t=743477) 

I have set up an old machine as a server running debian. as part of the install I set up xorg and fluxbox to give me a basic graphical interface. Now that it's running ok, I want to run it without the extra resource that a graphical interface consumes.
I though that if I modified 

> # The default runlevel.
id:5:initdefault:


to

> # The default runlevel.
id:3:initdefault:


in /etc/inittab that would stop x from starting, but it doesn't:mad: (I've also tried 2 and 4).
Can anyone help me to run an X-free box please ?

---

### Post by bingoUV on 2008-04-17
From Add/Remove Software, why don't you remove X server? Removing  xorg server, and everything that depends on it should do what you want.

---

### Post by happypig on 2008-04-17
I could do that, but I still want it there, I just don't want it to start automatically

---

### Post by y-lee on 2008-04-17
[preventing X from starting]("http://www.howtogeek.com/howto/ubuntu/prevent-xorg-from-starting-in-ubuntu/")

---

### Post by bodhi.zazen on 2008-04-17
Oh, that tutorial will work, but it is less then ideal, although update-rc.d is the way to go. Notice how when you re-configure the defaults change  (it changed S13gdm to S20gdm).

At any rate, in Ubuntu you should understand a few things.

Very briefly, Ubuntu no longer users System V boot scripts, it uses upstart. It is back compatible to emulate System V scripts.

Second, in Ubuntu, init 2 = inti 3 = init 4 = init 5, ie unlike other distros.

Last, keep in mind Linux is case sensitive. Thus, to disable X ...

The default "run level" is 2

```
sudo mv /etc/rc2.d/S20gdm /etc/rc2.d/s20gdm
```

To start X just use "startfluxbox"

---

