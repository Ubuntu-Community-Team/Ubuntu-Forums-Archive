---
title: "HP Laserjet P1005"
date: 2014-08-24
forum: General Help
---

### Post by daniell59 on 2014-08-24
I cannot seem to add the printer. HP Laserjet P1005
With all past Ubuntus it was immediately recognized.
Ubuntu 14.04 32
Could it be because past OS were 64 bit?

Thanks

---

### Post by ibjsb4 on 2014-08-24
hplip ??

[ATTACH=CONFIG]255805[/ATTACH]

---

### Post by daniell59 on 2014-08-25
I am somewhat confused. As I previoulsy stated, with all of my other ubuntu installations, the printer was immediately detected. Could it be that it needs a 64 bit OS?

---

### Post by mozalmy on 2014-08-25
You may need to install hplip.

Download from here: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

Installer walkthrough: [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

After installing hplip you would be able to add your printer.

---

### Post by Ksiencha on 2014-08-25
I really don't know what's wrong, but in previous versions of OS I also had my hp laserjet p1006 recognized immediately. I haven't used my printer in a long time, so I've installed drivers today using the following commands with plugged-in printer:

```

sudo apt-get install hplip
sudo hp-setup -i

```

I simply followed the instuctions of that setup manager in terminal and my printer works now! I'm sure it'll work for yours, p1005 is a minor difference in this case.
**Note!** there were two questions *[Enter additonal information or notes for this printer]* and another one after that (don't remember): I left them empty and hit **Enter** on those questions, don't hit **quit**.

Good luck ;)

---

### Post by daniell59 on 2014-08-25
I tried all of the suggestions. So far nothing has worked. I am thinking about re-installing. Perhaps I will go back to 12.04.

---

### Post by Ksiencha on 2014-08-25
If you re-install Ubuntu 14.04 and get to work your printer, it'd be nice to know another solution to the problem.

---

### Post by daniell59 on 2014-08-25
Oh, am I dumb. I am ashamed to admit it. I exchanged computers with my wife so that I can work on hers. I did not realize that the USB cable was not plugged into the computer. Please forgive me for those that went throught the trouble to help.

---

### Post by Ksiencha on 2014-08-25
No worries, it made me to finally find my solution in this case, because till this day, I haven't configured my printer, and had no idea that manager doesn't work automatically now. So thank you anyway ;)

---

