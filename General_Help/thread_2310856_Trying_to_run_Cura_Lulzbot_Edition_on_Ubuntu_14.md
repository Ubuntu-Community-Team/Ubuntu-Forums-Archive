---
title: "Trying to run Cura Lulzbot Edition on Ubuntu 14"
date: 2016-01-22
forum: General Help
---

### Post by Steve_Cline on 2016-01-22
I am trying to run the slicer software Cura 17.10 on Trusty.  I have tried several install methods from this instruction page [https://www.lulzbot.com/learn/tutorials/cura-lulzbot-edition-installation-debian](https://www.lulzbot.com/learn/tutorials/cura-lulzbot-edition-installation-debian).

I have apparently installed the software as it shows up on a search but it will not open in any way.

Does anyone have experience with this type of install?  I use Linux fairly often but I still think I am pretty much a novice.

Thanks for your advice.

---

### Post by Nuno_Abreu on 2016-01-22
Could you please tell me the output of **cura** in the Terminal? That probably would help a lot.

---

### Post by dragonfly41 on 2016-01-22
Seems that installation requirements are Ubuntu 14.10 or newer .. what Ubuntu version are you using?

---

### Post by Vladlenin5000 on 2016-01-22
> **dragonfly41 said:**
> Seems that installation requirements are Ubuntu 14.10 or newer .. what Ubuntu version are you using?

Already in the OP:
> I am trying to run the slicer software Cura 17.10 on [COLOR=#b22222]Trusty[/COLOR].
Trusty = 14.04 and that explains it.

---

### Post by bab1 on 2016-01-22
> **dragonfly41 said:**
> Seems that installation requirements are Ubuntu 14.10 or newer .. what Ubuntu version are you using?
Why do you say that?  From the[** OP's link**]("https://www.lulzbot.com/learn/tutorials/cura-lulzbot-edition-installation-debian")
```
If using Debian Wheezy or Ubuntu [COLOR="#FF0000"]Trusty[/COLOR]:

    sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak && sudo sed -i '$a deb http://download.alephobjects.com/ao/aodeb wheezy main' /etc/apt/sources.list && sudo apt-get update && sudo apt-get install cura

```

---

### Post by dragonfly41 on 2016-01-22
> [COLOR=#000000]Why do you say that?[/COLOR]
I was just referring to this .. [https://www.lulzbot.com/cura](https://www.lulzbot.com/cura)
> [COLOR=#666666][FONT=titillium_regular]Ubuntu 14.10 or newer[/FONT][/COLOR]
and wondering if there was some package in 14.10 which is not in 14.04 (for example).

[later edit]
I read this just out of interest .. [https://ultimaker.com/en/community/16843-for-the-ubuntu-1404-lts-users](https://ultimaker.com/en/community/16843-for-the-ubuntu-1404-lts-users)

---

### Post by bab1 on 2016-01-22
> **dragonfly41 said:**
> I was just referring to this .. [https://www.lulzbot.com/cura](https://www.lulzbot.com/cura)

and wondering if there was some package in 14.10 which is not in 14.04 (for example).

[later edit]
I read this just out of interest .. [https://ultimaker.com/en/community/16843-for-the-ubuntu-1404-lts-users](https://ultimaker.com/en/community/16843-for-the-ubuntu-1404-lts-users)I t sure looks like a Web Page typo and/or lack of update  to me.  The minimum version of Ubuntu should 15.10 not 14.10.

---

