---
title: "[SOLVED] wanted: good documentation on using dpkg-reconfigure xserver-xorg"
date: 2007-12-31
forum: General Help
---

### Post by erfahren on 2007-12-31
despite my searching I can't seem to find good, thorough (and easy to understand), documentation on reconfiguring the X Server using dpkg-reconfigure xserver-xorg

like what to expect, command line options for it, (also, maybe when it's really needed).

I've searched for a good doucumentation on it for myself and also when suggesting that others use it, but everything I've found is very complex or doesn't have much about it. a couple I've found were these: 
[http://www.mepis.org/docs/en/index.php/Dpkg-reconfigure_xserver-xorg](http://www.mepis.org/docs/en/index.php/Dpkg-reconfigure_xserver-xorg)
[http://wiki.freespire.org/index.php/Reconfigure_a_Broken_Xorg_Server](http://wiki.freespire.org/index.php/Reconfigure_a_Broken_Xorg_Server)

does anyone know of any other guides? Does a thorough (but simple) one need to be made?

---

### Post by zvacet on 2007-12-31
Maybe [this](https://help.ubuntu.com/community/FixVideoResolutionHowto) can be helpfull to you,but if you just want to change your driver accept all defaults and when you come to driver stage pick one you want.

---

### Post by erfahren on 2007-12-31
> **zvacet said:**
> Maybe [this](https://help.ubuntu.com/community/FixVideoResolutionHowto) can be helpfull to you,but if you just want to change your driver accept all defaults and when you come to driver stage pick one you want.
thank you for the link

I have a question about the options...

in that documentation it shows using "-plow" with it
```

sudo dpkg-reconfigure -plow xserver-xorg

```
I've also seen it as:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
I read somewhere that the second way sets all the defaults and goes directly to set the resolution, but also read that it goes directly to set the video driver. 

what do those options do? (goiing directly to the video driver would be helpful in many situations I think).

---

### Post by pointone on 2007-12-31
The "-p*" option stands for priority, and it specifies the minimum priority of question that will be displayed. Running with -plow (--priority=low) will ask every question and allow you full control of the configuration. Running with -phigh (--priority=high) or -pcritical (--priority=critical) will force debconf to automatically answer lower-priority questions using sensible defaults, and only ask the really important questions (i.e., ones without defaults).

---

### Post by erfahren on 2007-12-31
> **pointone said:**
> The "-p*" option stands for priority, and it specifies the minimum priority of question that will be displayed. Running with -plow (--priority=low) will ask every question and allow you full control of the configuration. Running with -phigh (--priority=high) or -pcritical (--priority=critical) will force debconf to automatically answer lower-priority questions using sensible defaults, and only ask the really important questions (i.e., ones without defaults).
lol - oh!

I didn't really notice that one was -p*low* and the other was -p*high*

that makes sense. thanks

---

### Post by AndyCooll on 2007-12-31
If you're having trouble with your graphics card, as has already been mentioned just accept all the defaults ...except when it comes to the graphics card section. You could then choose the one you want (as has been mentioned), however if that has been causing problems choose VESA instead. It's a bog standard graphics card setting that will at least get you a gui. You can then always play around again until you get everything optimised to your satisfaction (in the knowledge that you can always drop back to the VESA configuration if all goes wrong and you need to start again).

:cool:

---

### Post by erfahren on 2007-12-31
actually, (maybe I should clarify this) I wasn't really looking for documentaion for myself right now. 

It's just that I've suggested to others to use it when they couldn't get X to start or whatever, but have only used it a couple time myself. 

I always wanted to link to some good documentation on it so they'd know what to expect, but never really found any.

---

### Post by erfahren on 2008-01-05
I'm an idiot!

I just found the type of gude I was looking for. There's one at Hermanzone's site which I access and link to all the time, but never noticed it. (in my defense, he has a lot of info there!)

[Hermanzone's guide on dpkg-reconfigure xserver-xorg](http://users.bigpond.net.au/hermanzone/p7.html)

---

