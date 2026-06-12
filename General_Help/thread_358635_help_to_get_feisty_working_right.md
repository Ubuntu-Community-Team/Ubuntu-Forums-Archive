---
title: "help to get feisty working right"
date: 2007-02-11
forum: General Help
---

### Post by thecucchi on 2007-02-11
I'm having trouble getting everything to work right in feisty herd 3 i did a clean install
here is what my computer specs are
Intel® Core 2 Duo T7200 (2.00GHz, 4MB L2 Cache, 667MHz FSB)
]256MB ATI MOBILITY  RADEON® X1400 HyperMemory
is there any drivers for this card
i tried this [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Enable_.22restricted.22_Repository](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Enable_.22restricted.22_Repository)
but beryl keeps crashing does anyone have any ideas

---

### Post by happy-and-lost on 2007-02-11
fglrx does not support composite extensions (and therefore beryl)

The [Radon Driver]("https://help.ubuntu.com/community/RadeonDriver"), however, does :)

---

### Post by cstrippie on 2007-02-11
You machine is identical to mine in the specs you list.  The standard fglrx driver works fine with beryl, and is the only way you're going to get beryl working.  What we need to do is troubleshoot this in real time to see where things went wrong, so drop by #beryl on irc.freenode.net and we can probably get this worked out for you.  When you arrive, look for xsacha, racarr, or myself.

happy-and-lost: fglrx works *perfectly* in beryl, and the radeon driver does not support the x1400 - please educate yourself prior to spouting useless & inaccurate crap.

---

### Post by thecucchi on 2007-02-12
what is irc.freenode.net??? can some one point me in the right direction here my card is not supported by the radeon driver and i want to run beryl

---

### Post by cstrippie on 2007-02-13
irc.freenode.net is an irc chat server.  Normally used with something like xchat, you can also use the preinstalled GAIM to access it.

Alternatively, you can follow the instructions here: 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29)

The guide is meant for edgy, but I have used it on both edgy and feisty.

---

### Post by llamakc on 2007-02-13
There is a forum here for Fiesty discussions.

[http://ubuntuforums.org/forumdisplay.php?f=179](http://ubuntuforums.org/forumdisplay.php?f=179)

---

