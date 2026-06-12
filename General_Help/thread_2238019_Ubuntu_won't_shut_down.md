---
title: "Ubuntu won't shut down"
date: 2014-08-05
forum: General Help
---

### Post by stuapdoom on 2014-08-05
Hi, new user here. I just installed Ubuntu on my Acer Travelmate laptop. Everything seems fine until I try to shut down. I click 'Shut down', but I just get a black screen with the Ubuntu logo. I've searched the forum and found some answers, but I don't understand some of the terminology.

Can anyone help, please?

---

### Post by stalkingwolf on 2014-08-05
id start with running the recovery mode and fix broken packages sometimes thats all thats needed.. also hard wire it if possible when doing this.

---

### Post by stuapdoom on 2014-08-05
I've tried several ways to start in recovery mode - unsuccessfully! :(

---

### Post by whitesmith on 2014-08-05
This may not work, but its worth a try. Have a look at the AptGet/Howto ([https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)). In the Maintenance Commands section, try running the commands in sections 1-7 in exactly that order. Regards.

---

### Post by stuapdoom on 2014-08-05
> **whitesmith said:**
> This may not work, but its worth a try. Have a look at the AptGet/Howto ([https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)). In the Maintenance Commands section, try running the commands in sections 1-7 in exactly that order. Regards.

This is a bit too advanced for me, I'm afraid. :confused:

---

### Post by whitesmith on 2014-08-05
No need to be afraid. The commands are all tried and true, since they are on an Ubuntu site. I've used these same commands myself, and on a number of machines, to get out of sticky situations. Look at it this way: Of what value is an installation that doesn't shut down? Think of the words that describe it. Aren't you thinking of something along the lines of *useless*? Besides, if my advice were wrong, a dozen other guys who regularly comment on the forum would long ago have jumped in and told you **Stop!** Summon the will to give it a try. Even if it doesn't solve your problem, you will have learned something about Linux. I'll monitor this thread for a while to help out should you have a problem. Cheers.

---

### Post by stuapdoom on 2014-08-06
OK, I tried that, and after I entered command 1, this is waht appeared on screen:

[I]E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directore (/var/lib/dpkg/). are you root?[/I]

---

