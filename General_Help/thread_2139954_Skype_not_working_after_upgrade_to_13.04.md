---
title: "Skype not working after upgrade to 13.04"
date: 2013-04-26
forum: General Help
---

### Post by CyberAngel on 2013-04-26
Same problem for after I upgraded to 13.04 yesterday :(

---

### Post by xc3RnbFO8P on 2013-04-26
> **CyberAngel said:**
> Same problem for after I upgraded to 13.04 yesterday :(

Try to start Skype from Terminal window with this:
>  LD_PRELOAD=/usr/lib/i386-linux-gnu/mesa/libGL.so.1 skype

---

### Post by CyberAngel on 2013-04-26
I downgraded libqtwebkit4 to version 2.2.1 and it is working now!

---

### Post by obadz on 2013-04-27
Create a file /etc/apt/preferences.d/skype-1100

Put this in it:
```
Package: libqtwebkit4
Pin: release n=quantal
Pin-Priority: 1100
```

More on package pinning [here]("https://help.ubuntu.com/community/PinningHowto").

Add quantal repos in your sources:

```
sed s/raring/quantal/g < /etc/apt/sources.list | sudo tee /etc/apt/sources.list.d/quantal.list
```

Then, ```
sudo apt-get update && sudo apt-get upgrade
```
... should eventually tell you:
```
The following packages will be DOWNGRADED:
  libqtwebkit4
```

Good luck.

---

### Post by stevedude on 2013-04-27
Proprietary Nvidia and AMD drivers are causing this known bug. Go to [http://www.webupd8.org/2013/04/fix-skype-not-working-in-ubuntu-1304.html](http://www.webupd8.org/2013/04/fix-skype-not-working-in-ubuntu-1304.html) and follow the instructions. It worked for me.

---

### Post by bmbaker on 2013-04-28
Actually its not just Proprietary Nvidia and AMD drivers are causing this known bug i have the same on my install which is intel graphics,
none of the solutions work for i still keep getting

```
skype
Segmentation fault (core dumped)
```

---

### Post by Elfy on 2013-04-28
Moved out of Dev forum to General Help.

---

### Post by obadz on 2013-05-01
Latest skype upgrade (4.1.0.20.0-0ubuntu0.12.04.2) fixes this for me. I no longer need the package pin.

---

