---
title: "Automatix = troublemaker [Help ASAP]"
date: 2007-03-20
forum: General Help
---

### Post by Andrew33 on 2007-03-20
Hi,

about 30 minutes ago I had downloaded Automatix and decided to install many applications for my computer. I have installed the following:

- Multimedia codec
- Nvidia driver? (this might be the cause of the problem)
- Google Earth
- Open Office clipart
- audicity

And a few others.

However, after I restarted the computer when the applications were "successfully" installed, my computer remains at a black screen after the Ubuntu logo on the loading screen.

I tried to look around for solutions and found out that you can work your way to uninstall some of the things, such as the NVidia driver, but I'm not exactly sure how I can do so (i'm a Linux newbie).

Any help would be muchly appreciated!

---

### Post by depele on 2007-03-20
==> yeah I've been there done that! had same problems.

check your x-org config to see if anyting is wrong. or strange, you can also post it here.

Ohterwise you can try to remove the by automatix installed programs and install them manually. 
```

sudo apt-get remove automatix
```

not sure if it deletes the packages installed by automatix

More work but better effect. 

good luck.

---

### Post by jackrobinson on 2007-03-20
> **Andrew33 said:**
> Hi,

about 30 minutes ago I had downloaded Automatix and decided to install many applications for my computer. I have installed the following:

- Multimedia codec
- Nvidia driver? (this might be the cause of the problem)
- Google Earth
- Open Office clipart
- audicity

And a few others.

However, after I restarted the computer when the applications were "successfully" installed, my computer remains at a black screen after the Ubuntu logo on the loading screen.

I tried to look around for solutions and found out that you can work your way to uninstall some of the things, such as the NVidia driver, but I'm not exactly sure how I can do so (i'm a Linux newbie).

Any help would be muchly appreciated!
[http://www.getautomatix.com/forum/index.php?showtopic=725&view=findpost&p=2089](http://www.getautomatix.com/forum/index.php?showtopic=725&view=findpost&p=2089)

---

### Post by Andrew33 on 2007-03-20
> **depele said:**
> ==> yeah I've been there done that! had same problems.

check your x-org config to see if anyting is wrong. or strange, you can also post it here.

Ohterwise you can try to remove the by automatix installed programs and install them manually. 
```

sudo apt-get remove automatix
```

not sure if it deletes the packages installed by automatix

More work but better effect. 

good luck.

I removed automatix, but that did not solve the issue. I'm new to ubuntu, and I have no clue how to check my x-org config or whatever and see any issues within it.

> [http://www.getautomatix.com/forum/in...indpost&p=2089](http://www.getautomatix.com/forum/in...indpost&p=2089)

The website seems to be down. :(

Any more help would be appreciated!

---

