---
title: "Winfast tv2000 problem!"
date: 2007-09-09
forum: General Help
---

### Post by rabelj on 2007-09-09
I instaled ubuntu software for my Tv 2000 xp rm card. Before instilation sound was working fine in winfastpvr. But now when i instaled Ununtu i dont have sound when i watching tv(in winfastpvr and Ubuntu). What can i do? (In windows media player sound work fine I have problems youst when i"m watching tv)

---

### Post by kylomax on 2007-09-14
can you help? how do ypu instal winfasttv as i have misplaced winfattv cibstalation cd?

---

### Post by JBAlaska on 2007-09-14
The drivers and manual are available at there site:
```
http://www.leadtek.com.tw/eng/support/list_driver.asp
```

Here's a howto on installing in ubuntu;
```
http://clau.sparetimegroup.net/index.php/ubuntu/winfast-2000-xp-rm-on-ubuntu/
```

---

### Post by nikoPSK on 2007-09-26
How did you get it to work? If you used a how-to please send me the link. because I have a tv 200 xp series as well and I don't know what to use for watching the tv (program) and where do I get drivers (if I need them).:KS

Thanks,
Niko

---

### Post by SeanTater on 2007-09-26
I just set up the RM model about 3 days ago. Ubuntu Feisty recognized it perfectly with one exception, in my case, it assumed that I live in Europe, and use the PAL format. I changed it to North America's NTSC format by doing the following. 

```

sudo rmmod bt878
sudo rmmod bttv
sudo modprobe bttv card=34 tuner=43

```

Then open up kdetv or tvtime (both in the repositories), and set up channels (for kdetv), then enjoy.

However -- I tried to edit /etc/modules and it does not appear to work at startup, though the longs did not seem to shed light on why. Unfortunately, you will likely need to enter this at every reset, or find some other way. I only reset every 1 to 6 months so that does not make too much of a difference to me..

One important note: before executing that, all your TV programs must be off, and in some cases you might have to do a hard reset. It seems to lock up some part of process management, but I don't know how, it may be specific to me..

---

### Post by nikoPSK on 2007-09-26
I need to find the card number and channel number. 
[http://www.linuxtv.org/v4lwiki/index.php/Cardlist.BTTV]("http://www.linuxtv.org/v4lwiki/index.php/Cardlist.BTTV")
[http://www.linuxtv.org/v4lwiki/index.php/Tuners]("http://www.linuxtv.org/v4lwiki/index.php/Tuners")

Once again Winfast TV2000 XP series:KS

---

### Post by nikoPSK on 2007-09-28
nvm found it, but no sound in tvtime:confused:

---

### Post by buksnatata on 2008-03-02
did someone managed to solve start up problem with modules? plz help

---

### Post by nikoPSK on 2008-03-04
> **buksnatata said:**
> did someone managed to solve start up problem with modules? plz help
As I keep saying remove the wrong modules, put the right ones and bingo. To load at startup:

sudo gedit /etc/modprobe.d/bttv

options bttv card=34 tuner=43

blam,

---

