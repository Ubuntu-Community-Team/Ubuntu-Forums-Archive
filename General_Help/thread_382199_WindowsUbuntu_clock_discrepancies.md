---
title: "Windows/Ubuntu clock discrepancies"
date: 2007-03-11
forum: General Help
---

### Post by jordon on 2007-03-11
I'm running XP and Edgy on the same machine. When I boot into Windows, the clock is four hours ahead of the actual time. If I fix the time and then boot into Ubuntu, the clock is four hours behind. This upsets the Windows time, and it goes on like a vicious cycle. Both systems' time zones are set to Eastern Daylight Time (UTC -4), but I think one or both are misinterpreting the CPU clock's time zone.

A friend recommended, when Ubuntu's clock is running behind, to have it display the time as UTC. This is not acceptable to me because the actual system time remains incorrect and, for example, timestamps in Gaim remain thrown off by four hours.

So how do I fix this the right way?

---

### Post by SuSUntu on 2007-03-11
Not sure if I understand your UTC setup based on your post, but this problem is usually caused by setting Ubuntu (other distros as well) to use UTC. 

Ubuntu gives you the choice to set UTC or not during installation, and if you selected UTC time, your Windows / Ubuntu clocks will keep messing each other up.

You can check this file:

```

sudo gedit /etc/default/rcS

```

to see whether **UTC=yes**. If so change it to **UTC=no**  

Simply changing the clock preferences to **display** UTC is not the same effect as editing this file.

I first experienced this 'gremlin' with Suse years ago, and ever since, I make sure to set the distros I install in multi-boot environments to not use UTC during the installation process.

Hope this helps.

---

### Post by jordon on 2007-03-12
I set Ubuntu's clock to be right and made the edit as you suggested, and Windows now shows the right time. Thanks!

---

### Post by John RG on 2007-03-28
Works for me too- thanks

---

### Post by mikecoal on 2007-11-08
Worked for me too!
Thanks!

---

### Post by rajeshwar on 2008-04-20
Hey... thanks. Worked for me. I had this nasty problem of make not working properly because the files were "altered" in future. Guess that won't happen anymore.

---

### Post by archer6 on 2008-06-13
> **SuSUntu said:**
> Not sure if I understand your UTC setup based on your post, but this problem is usually caused by setting Ubuntu (other distros as well) to use UTC. 

Ubuntu gives you the choice to set UTC or not during installation, and if you selected UTC time, your Windows / Ubuntu clocks will keep messing each other up.

Thanks for the well written, clear explanation. You made it easy. 
And I appreciate your clearly written code, as this is all new to me. 
I followed your suggestion and now my clock keeps perfect time!
You just made a new Linux user very happy!

I will clicking the "thanks" button on your original post of this. 

Cheers!

---

