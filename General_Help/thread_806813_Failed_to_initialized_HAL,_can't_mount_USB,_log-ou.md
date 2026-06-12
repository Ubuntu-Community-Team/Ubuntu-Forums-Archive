---
title: "Failed to initialized HAL, can't mount USB, log-out icon locks-ups"
date: 2008-05-25
forum: General Help
---

### Post by geekATlarge on 2008-05-25
I've been using this installation of ubuntu since 7.04, and I've loaded it full of goodies. After the 8.04 upgrade, it has caused me great pains.
- at startup, an icon "Failed to initialize HAL"
- unable to automatically mount USB devices
- the log-out icon freeze gnome

Well, I didn't want to reinstall everything so I had to find the solution.  Here it is.

During the linux startup, gnome is started before its dependencies (i believe its HAL). I can't explain why my system has this problem and not every other. Maybe, cause its an orginal installation of 7.04 ...

these were my gdm startup scripts, with a startup priority of 13
```

$ ls /etc/rc*/*gdm
/etc/rc0.d/K01gdm  /etc/rc2.d/S13gdm  /etc/rc4.d/S13gdm  /etc/rc6.d/K01gdm
/etc/rc1.d/K01gdm  /etc/rc3.d/S13gdm  /etc/rc5.d/S13gdm

```
Hal has a priority of 24, and the highest number in use was 25 (excluding the 89-99).

So ... remove the gdm startup links
```
sudo update-rc.d -f gdm remove
 Removing any system startup links for /etc/init.d/gdm ...
   /etc/rc0.d/K01gdm
   /etc/rc1.d/K01gdm
   /etc/rc2.d/S13gdm
   /etc/rc3.d/S13gdm
   /etc/rc4.d/S13gdm
   /etc/rc5.d/S13gdm
   /etc/rc6.d/K01gdm

```

create new startup gdm links. I choose a priority of 26, this will depend on what is installed in your system. The higher the number, the later it is starter in the startup sequence. Look at your /etc/rc5.d directory and choose a number that is greater the HAL number (S24hal on mine). I choose the next greatest number that was not in the 89-99 range.
```

sudo update-rc.d gdm defaults 26 1
 Adding system startup for /etc/init.d/gdm ...
   /etc/rc0.d/K01gdm -> ../init.d/gdm
   /etc/rc1.d/K01gdm -> ../init.d/gdm
   /etc/rc6.d/K01gdm -> ../init.d/gdm
   /etc/rc2.d/S26gdm -> ../init.d/gdm
   /etc/rc3.d/S26gdm -> ../init.d/gdm
   /etc/rc4.d/S26gdm -> ../init.d/gdm
   /etc/rc5.d/S26gdm -> ../init.d/gdm

```

now your startup scripts should look like this
```

# ls rc*/*gdm*
rc0.d/K01gdm  rc2.d/S26gdm  rc4.d/S26gdm  rc6.d/K01gdm
rc1.d/K01gdm  rc3.d/S26gdm  rc5.d/S26gd

```

Reboot your machine see if it fixes the problems.

I hope someone finds this usefull.

---

### Post by chrisccoulson on 2008-05-25
Instead of doing this, you can just upgrade to the new gdm package in hardy-proposed which sets the gdm symlink priority to 30. This fixes [bug 227838]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/227838")

---

### Post by geekATlarge on 2008-05-25
Chris, thanks for your reply. I changed the priority to 30. hardy-proposed is the beta-version of the update repository, right? I'm looking to stability and will wait for the release.

---

### Post by chrisccoulson on 2008-05-25
hardy-proposed is a testing repository for upgraded packages, so you should be careful what you install from it. However, if you're after stability, then manually changing symlink priorities won't get you that. In fact, in this case, changing the symlink priority to anything other than 13 or 30 for gdm could have broken gdm updates for you in the future, due to the way the install scripts work

---

### Post by BioGeek on 2008-05-25
And how exactly do I upgrade to new gdm package in hardy-proposed?

In [bug #227838]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/227838") they mention that "gdm 2.20.6-0ubuntu2" fixes the problem, so I guess that's the newest gdm package that chrisccoulson is talking about. 

But it seems like I have that version already installed:

```
$ gdm --version
GDM 2.20.6

```

And I still get the "Failed to initialized HAL error".

So, is there an obvious way to upgrade to the new gdm package in hardy-proposed that I'm missing, or should I start messing with my symlink priorities anyway?

Thanks in advance!

---

### Post by chrisccoulson on 2008-05-26
Go to System -> Software Sources, then click the 'Updates' tab and make sure 'Proposed Updates' is checked.

'gdm --version' will tell you that 2.20.6 is installed because the proposed update is only bumps the version from 2.20.6-0ubuntu1 to 2.20.6-0ubuntu2.

If you want to be really sure, then do:
```
apt-cache policy gdm
```

---

