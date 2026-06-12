---
title: "starting x automatically at boo"
date: 2007-09-21
forum: General Help
---

### Post by chocolatetoothpaste on 2007-09-21
Hey all,
  I just installed a fresh copy of Ubuntu with only the command line.  my goal is to install fluxbux and have a nice clean setup.  Here's the problem:  what's the best way to do this?  I can get fluxbox compiled and installed ok, but how do I get x to start automatically?  I probably won't install a login manager, just text.  So in what script and where should I startx?

---

### Post by yabbadabbadont on 2007-09-21
Probably as the last line of your ~/.profile.

---

### Post by chocolatetoothpaste on 2007-09-21
> **yabbadabbadont said:**
> Probably as the last line of your ~/.profile.

Thanks for the speedy response.  Is there a more universal location?  I know /etc/profile is the first to run, i just am not sure if it's the best place to put it.  I did put it in there to test it, and it worked, i just don't want conflicts down the road.

---

### Post by yabbadabbadont on 2007-09-21
> **chocolatetoothpaste said:**
> Thanks for the speedy response.  Is there a more universal location?  I know /etc/profile is the first to run, i just am not sure if it's the best place to put it.  I did put it in there to test it, and it worked, i just don't want conflicts down the road.

/etc/profile can be replaced during system updates.  Your personal .profile won't be.

---

### Post by kerry_s on 2007-09-21
> **chocolatetoothpaste said:**
> Hey all,
  I just installed a fresh copy of Ubuntu with only the command line.  my goal is to install fluxbux and have a nice clean setup.  Here's the problem:  what's the best way to do this?  I can get fluxbox compiled and installed ok, but how do I get x to start automatically?  I probably won't install a login manager, just text.  So in what script and where should I startx?

~/.bash_profile

i use->

```
[B]if [ `tty` = "/dev/tty1" ]; then
startx
fi
[/B]
```

that will start X after you log in.

for auto log in you need to change the /etc/event.d/tty1

see this thread-> [http://ubuntuforums.org/showthread.php?p=3348011#post3348011](http://ubuntuforums.org/showthread.php?p=3348011#post3348011)

---

### Post by yabbadabbadont on 2007-09-21
> **kerry_s said:**
> ~/.bash_profile

i use->

```
[B]if [ `tty` = "/dev/tty1" ]; then
startx
fi
[/B]
```

Hmmm.  Good safety tip.  (and it lets you switch to tty[2-6] and login without causing problems.  Nice.)

---

### Post by kerry_s on 2007-09-21
> **yabbadabbadont said:**
> Hmmm.  Good safety tip.  (and it lets you switch to tty[2-6] and login without causing problems.  Nice.)

i only leave tty2 for backup, all the rest of mine are commented out, i've never had to use them.

my debian /etc/inittab

1:2345:respawn:/sbin/mingetty tty1 --autologin user
2:23:respawn:/sbin/getty 38400 tty2
#3:23:respawn:/sbin/getty 38400 tty3
#4:23:respawn:/sbin/getty 38400 tty4
#5:23:respawn:/sbin/getty 38400 tty5
#6:23:respawn:/sbin/getty 38400 tty6

---

