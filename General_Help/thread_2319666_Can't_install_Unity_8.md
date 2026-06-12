---
title: "Can't install Unity 8"
date: 2016-04-06
forum: General Help
---

### Post by madevcic on 2016-04-06
I tried to install unity 8, but keep getting this error.

```
The following packages have unmet dependencies:
 unity8-desktop-session-mir : Depends: unity8 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```
I tried searching for held packages, but the list is empty.

I'm installing with this command
```

sudo apt-get upgrade && sudo apt-get dist-upgrade
sudo apt-get install unity8-desktop-session-mir

```
[COLOR=#000000][FONT=Monaco][FONT=inherit]
[/FONT]

[/FONT][/COLOR]

---

### Post by grahammechanical on 2016-04-06
What version of Ubuntu are you trying this on?

I have no problem installing Unity8-desktop-session-mir but 14.04 was the last version of Ubuntu where I could get past the login screen with Unity8. And I have tried all versions since 14.04.

I tried again recently on 16.04 development version (xenial xerus). And just 2 days ago I put in a fresh install of xenial and installed unity8-lxc and that installed seemingly fine but again the session will not start and move past the login screen. In this case it will not start the LXC container that Unity 8 is supposed to run in. By the way, you are using an open source video driver. Are you? Won't work with proprietary video drivers.

To fix held broken packages

```
sudo apt-get install -f
```

From my own personal experience, this promise that in 16.04 we will be able to load into a Unity 8 session on Mir is not something any Ubuntu developer should be bragging about.

Regards.

---

### Post by madevcic on 2016-04-07
I'm running 15.10
Tried that command also ... but no luck

---

### Post by slickymaster on 2016-04-07
*Moved to the ***General Help*** sub-forum*

---

### Post by Peter_Linzbauer on 2016-05-25
Hi, i think i got the same problems on 16.04. I solved it. First I tried the usual things like:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
sudo apt-get -f install
```
This commands did not work for me, maybe the work for someone else who is searching this.

I found my solution with a kind of crude method. I just added the packages my console kept recommending, till I found the last one: **libandroid-properties1** (it said something about a wrong version number)
This is the way i went, but not the solution:
```

sudo apt-get install unity8-desktop-session-mir unity8-desktop-session-mir unity8 unity-scope-click ubuntu-system-settings indicator-network urfkill libhybris libandroid-properties1
```

The solution for me was just to remove the package and to install unity8

```

sudo apt-get remove libandroid-properties1
sudo apt-get autoremove
sudo apt-get install unity8-desktop-session-mir
```

---

