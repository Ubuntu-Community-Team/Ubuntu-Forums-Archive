---
title: "Wen't wrong after compiz"
date: 2008-04-13
forum: General Help
---

### Post by Firm18 on 2008-04-13
Ok so I Installed compiz with these:

[http://ubuntuchocolate.wordpress.com/2007/08/30/howto-install-compiz-fusion-on-ubuntu-feisty-fawn/](http://ubuntuchocolate.wordpress.com/2007/08/30/howto-install-compiz-fusion-on-ubuntu-feisty-fawn/)

and now I can't see my anything on my desktop (and my home folder when I go to the Desktop folder it shows everything). Everything seems to be running as metacity! Please I don't wont this, I wonna go back to my beryl and no this works like crap. What shell I do to make the thing bugger off. Each time I turn on my comp it doesn't show anything on the desktop and it's metacity...please help me...

Oh and I've just found out that I can't do anything with the desktop. I can't press right mouse....why?

---

### Post by starcannon on 2008-04-13
If you put /home on its own partition then my best advice would be to wait 11 days and put a fresh install of Ubuntu 8.04 Hardy Heron on there (compiz included and functional by default)

Otherwise sudo apt-get remove *any packages you installed using that guide*, restore your /etc/apt/sources.list file back to before, then sudo apt-get update, then synaptic package manager and put Beryl back on using genuine Ubuntu repositories.

Thats the short of it, I'm sure there will be some headaches here and there, you may need to delete some config files out of the /home/user directory (could even try that first just in case thats all thats wrong, letting them be auto rebuilt by the various software that use them)

If you don't have /home on its own partition you may want to consider resolving that as soon as time permits, it does require backing up your /home/user directory to external HDD or some other media first though, and then manually partitioning the drive during fresh install. Good partition scheme is 128mb for /boot, as much or double the amount of ram you have for /swap, 10+gb for /   root, and the rest for /home. The nice thing about /home on its own partition is that when (not if) you bugger things so badly that it would take longer to fix than to re-install, then its just as simple as formatting your /boot and /  root, resetting labels and NOT reformatting the /home and then continuing the re-install, when you get back in, it will all be set up as if whatever bad thing had never happened to you, even your wallpaper will be the same :)

Anyway, rambling along, GL, sorry your compiz experience is not working out, it really is nicer than Beryl imo, but at the end of the day use what works for you and what your happy with, thats truely the measure of good software.

---

### Post by Firm18 on 2008-04-13
Ok, cheers but could you write step by step what am I suppose to do? Couse I am a real newbie with linux and I don't won't to destroy sh else....please.

---

### Post by sekinto on 2008-04-13
For Metacity "metacity --replace"
For Beryl "beryl --replace"
For Compiz "compiz --replace"

---

### Post by Firm18 on 2008-04-13
I don't how I did it but I did what you told me to do guys and now it's back how it use to be...GOSH Thank You! You are good people! I am really greatfull...thank you, great site, great people. I've got only two questions. How can I make beryl default thing...that every time I turn the computer on beryl will be on to and it will be set as beryl not metacity? And If I update my Feisty to 7.10 will I loose everything? Or will I have everything on?

---

### Post by starcannon on 2008-04-13
Since you seem to have time this afternoon to geek out, then before you pass go, before you collect $200, before you do anything else, backup your /home/username directory to another HDD or to Several DVD's or whatever it takes. Then try doing a clean install of Gutsy being sure to put /home on its own partition (select manual during install) and use that partition strategy I posted. Taking the time now will save your sanity later.

Happy you were able to get things back to something useable and glad to be of assistance.

---

### Post by Firm on 2008-04-13
I always keep my most important thing on pendrive ;) So when I get sth wrong I've got them. And I have time now couse I got ill so I'm bored. Thank you for help, but will the update delete everything I installed and etc.

---

### Post by sekinto on 2008-04-13
To make Beryl start on login you can add "beryl --replace" to sessions (system>preferences>sessions).

You can either update or do a clean install if you want to get the latest version of Ubuntu. I would suggest waiting for Hardy though since the official release is in 11 days, instead of updating to Gusty that is.

---

