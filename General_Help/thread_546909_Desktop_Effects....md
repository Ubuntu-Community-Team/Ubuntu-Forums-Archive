---
title: "Desktop Effects..."
date: 2007-09-09
forum: General Help
---

### Post by jheinzman on 2007-09-09
How do i activate desktop effects?

Thanks...

                          -Jeff Heinzman

---

### Post by Amazona aestiva on 2007-09-09
Try Beryl. It often works well:
```
sudo apt-get install beryl beryl-manager
```

---

### Post by madcow72 on 2007-09-09
First, make sure that your video card is working with 3D acceleration.  In a terminal, type:
```
glxinfo | grep direct
```
and look for a response that says:
```
direct rendering: Yes 
```

If that is the case, then you just have to go to System -> Preferences -> Desktop Effects

---

### Post by madcow72 on 2007-09-09
You can't just install Beryl or Beryl-manager without adding them to your sources.list.  Anyway, Beryl has merged back with Compiz, and I wouldn't install it anyway as Compiz-Fusion (the new project) is way better and way more stable.

If the normal Desktop Effects that comes default with 7.04 works, then I would do a search on "Ubuntu Howto Compiz Fusion" and follow some directions on how to get that running.  First things first, however, make sure your video card is working and "Desktop Effects" work correctly.

---

### Post by FuturePilot on 2007-09-09
> **madcow72 said:**
> You can't just install Beryl or Beryl-manager without adding them to your sources.list.  Anyway, Beryl has merged back with Compiz, and I wouldn't install it anyway as Compiz-Fusion (the new project) is way better and way more stable.


Beryl is in the Ubuntu repositories. But true, it is no longer being developed.

---

### Post by madcow72 on 2007-09-09
> **FuturePilot said:**
> Beryl is in the Ubuntu repositories. 

Interesting, huh?  I didn't know that.  Is Compiz-Fusion also in the repositories?  Somehow that would make more sense to me.  Cool though!

---

### Post by FuturePilot on 2007-09-09
> **madcow72 said:**
> Interesting, huh?  I didn't know that.  Is Compiz-Fusion also in the repositories?  Somehow that would make more sense to me.  Cool though!

Not in Feisty but in Gutsy.

---

### Post by jheinzman on 2007-09-09
> **Amazona aestiva said:**
> Try Beryl. It often works well:
```
sudo apt-get install beryl beryl-manager
```

alright, i did that but i got this

```
jheinzman@pheinzman-desktop:~$ sudo apt-get install beryl beryl-manager
Password:
jheinzman@pheinzman-desktop:~$ 
```

---

### Post by Ub1476 on 2007-09-09
Just write your password. The text/asterisk is hidden so just press enter when finished. It should download and install.

---

### Post by Amazona aestiva on 2007-09-10
> **jheinzman said:**
> alright, i did that but i got this

```
jheinzman@pheinzman-desktop:~$ sudo apt-get install beryl beryl-manager
Password:
jheinzman@pheinzman-desktop:~$ 
```

This isn't what should happened!
If these are installed it should says something like this:
> nandor@nandor-desktop:~$ sudo apt-get install beryl beryl-manager
Password:
Csomaglisták olvasása... Kész
Függ&#337;ségi fa építése       
Állapotinformációk olvasása... Kész
beryl már a legújabb verzió.
beryl-manager már a legújabb verzió.
0 frissített, 0 újonnan telepített, 0 eltávolítandó és 0 nem frissített.
nandor@nandor-desktop:~$

If these aren't installed terminal should install them...
No idea...
Sorry

---

