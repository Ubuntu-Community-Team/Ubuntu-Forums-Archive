---
title: "Sysfsutils help."
date: 2008-04-21
forum: General Help
---

### Post by pinksoviet on 2008-04-21
Hi! I recently installed Ubuntu 7.10 Gutsy Gibbon on my Thinkpad T61p, and despite a few mishaps (including a certain accidental HDD wipe), everything is going quite nicely. However there is a certain problem that I can't seem to fix as of yet, and that involves sysfsutils.

I set it up to allow my trackpoint in /etc/sysfs.conf to allow for tapping of the trackpoint for a left button click (/devices/platform/i8042/serio1/serio2/press_to_select=1), and I also changed its sensitivity and speed, using the same thing albeit replacing press_to_select=1 with sensitivity and speed, respectively (and their respective values).

Same thing with my battery charging limits and whatnot. 

Now the problem lies in the fact that sysfsutils does not run at Ubuntu's startup (as I'd hope). I know the configuration works because if I run 

sudo /etc/init.d/sysfsutils start

then my trackpoint works as I'd set it to, and the battery charging measures take place. Oddly enough, when Ubuntu decided to do a random disk check (I don't know if this is random or if it's set to occur every 20 some odd start ups), my sysfsutils settings were enacted at start up. However, unless a disk check occurs or unless I manually type in sudo /etc/init.d/sysfsutils start in terminal, nothing occurs (in terms of the settings I put in).

Is there a way to make sysfsutils run at start up? If so, please help. This has been bugging me for a few days now. Also, just out of curiosity, does Ubuntu do automatic disk checks every so often? Or is it due to another reason?

Thanks in advance!

---

### Post by pinksoviet on 2008-04-22
Well, I tried adding it to the session manager to boot at start ( /etc/init.d/sysfsutils start), and it wouldn't work. 

Likewise, update-rc.d sysfsutils defaults told me that system startup links for sysfsutils already existed. Odd.

Thirdly, a person in the Ubuntu help chat on IRC told me to create a shell script and run it, which I did, and I gave it the appropriate permissions and set it as an executable, but still to no advail.

I encountered another disk check today, and like before, sysfsutils started perfectly once Ubuntu loaded after the disk check. When I rebooted, no such sysfsutils start ever occurred automatically.

If someone could help me, still, that would be greatly appreciated! Thank you!

---

### Post by pinksoviet on 2008-04-23
Bumpy bumpy.

---

### Post by pinksoviet on 2008-04-25
And another bump. Still a problem!

---

