---
title: "Use PS3 controller to replace mouse"
date: 2015-11-17
forum: General Help
---

### Post by bandito40 on 2015-11-17
Hi,

I am looking for a tutorial to use my PS3 controller in place of the mouse via bluetooth. I am looking to use the PS3 for all mouse operations and not just for video games. The only one that I have found says to install the *xserver-xorg-input-joystick* package but I not able to resolve the dependencies.

Thanks.

---

### Post by tgalati4 on 2015-11-18
Open a terminal.  Post the output of:

```
sudo apt-get install xserver-xorg-input-joystick
```

---

### Post by bandito40 on 2015-11-18
Thanks for replying.  It installs fine on my other computer running the same version of Ubuntu.  I copied the sources.list over but still getting the same problem. (Yes I did run apt-get update first) lol

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 xserver-xorg-input-joystick : Depends: xorg-input-abi-20
                               Depends: xserver-xorg-core (>= 2:1.14.99.902)
E: Unable to correct problems, you have held broken packages.

```

---

### Post by pqwoerituytrueiwoq on 2015-11-18
```
sudo apt-get install -f
```
if that does not fix it you will need to remove something you recently forced to installed (possibly a partial upgrade)

---

### Post by bandito40 on 2015-11-19
I tried downloading the dependencies directly as .deb files. The install was conflicting with something else that was installed. Hoping a fresh install will solve the problem.

---

### Post by stefilutz on 2016-03-15
I'm having the exact same problem. I tried EVERYTHING about [fixing unmet dependencies]("http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa"), but nothing worked.

---

