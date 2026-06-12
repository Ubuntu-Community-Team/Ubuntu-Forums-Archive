---
title: "How do I make Ubuntu Desktop headless?"
date: 2007-12-20
forum: General Help
---

### Post by nathandelane on 2007-12-20
I am actually working with gNewSense, which I know is based on Ubuntu, and isn't Ubuntu for various reasons, and for that I don't mind if you blow me off, but this question should apply to any Debian installation.

I have learned that in Debian, both runlevels 2 and 5 are equivalent, e.g. they both start up in X-Windows mode (kdm, xdm, gdm, etc. starts up with Linux). I also read that runlevel 3 should be console only with networking. I don't know whether that's true, but according the Debian.org it is.

So after having installed gNewSense, I changed the default runlevel from 2 to 3 in /etc/inittab, and when I rebooted, gNewSense still came up in X-Windows mode.

After that I asked on my local Linux Users Group mailing list what I should do to make my gNewSense installation headless, and they recommended running this command:

sudo update-rc.d -f kdm remove

which worked fine, except it removed kdm from all of my rc files, for every runlevel.

So what is the correct way to make a desktop installation of Debian, for example Ubuntu Desktop, headless, unless you run startx?

Thanks,

Nathan

---

### Post by pointone on 2007-12-20
All you really needed to do was remove the KDM-related script from the desired rc*.d directory. For example, to prevent KDM from starting in runlevel 3, simply remove /etc/rc3.d/S**kdm, where ** represents the sequence number.

I'm not sure what the default sequence number for KDM is, but on my install, GDM runs with sequence number 13 and stops with sequence number 01. 

Nonetheless, to have KDM start in runlevels 2, 4, and 5 (after removing it from every runlevel as you say you did) use the following command:

```
sudo update-rc.d kdm start 13 2 4 5 . stop 01 0 1 6 .
```

You will probably want to find out what the sequence numbers for KDM were on your installation and use that instead.

---

### Post by bodhi.zazen on 2007-12-20
Since Linux is cAse sEnsative,

sudo mv /etc/rc.3/SxxKDE /etc/rc.3/sxxKDE

Easy to restore and leeps track of # for you.

If you use update-rc.d I would :

```
sudo update-rc.d kdm start 13 2 4 5 . stop 01 0 1 3 6 .
```

Thus KDM stops if you boot to 2 and change to 3

---

