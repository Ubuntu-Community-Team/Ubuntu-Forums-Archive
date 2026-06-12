---
title: "Shutdown Without Display"
date: 2021-10-21
forum: General Help
---

### Post by suffring on 2021-10-21
I have a NUC10i5FNKN running Ubuntu 20.4. When the NUC is attached to a display and I press the on/off button the NUC shuts down without me having to do anything else. 
I want to use the NUC without a display. The problem is, it seems that without a display, pressing the on/off button won't shut the NUC down. I am told that if I use a HDMI dummy plug which tricks the NUC into thinking there is a display, it will close down. I also don't want to hold the on/off button for the extra time to cause a hard shutdown.
Is there a solution to shutting down the NUC without using a dummy plug and by pressing the on/off button?
Thanks in advance and cheers

---

### Post by TheFu on 2021-10-22
ssh in from another system and run:
**sudo shutdown -h now**

---

### Post by suffring on 2021-10-25
Thanks. I'll keep this up my sleeve but was really hoping for a way of simply using on/off button .

---

### Post by TheFu on 2021-10-25
> **suffring said:**
> Thanks. I'll keep this up my sleeve but was really hoping for a way of simply using on/off button .

I figured you had tried pushing a button already and it wasn't working.
Have you setup the logind.conf file under /etc somewhere already? It has settings for all sorts of actions.  You can read more about that in the manpage.  
**man logind.conf** has the details.  Probably interesting in the HandlePowerKey=, HandleSuspendKey=, HandleHibernateKey=, HandleLidSwitch=, HandleLidSwitchDocked= options and it is worth reading the next section about Inhibited buttons.  Because the version of logind on your system could be different from mine, definitely check your local manpage - don't google it.  The one actually on your box is the reference to be used.  You can use **xman** if you want a GUI, but the data provided is identical.

Perhaps it isn't calling the correct routine and using an alternate method would work.  Then, you can hook up a button to call the routine that works?  If the one above doesn't work, there are a few others.  In theory, they should all be directed to the same lower-level call with lots of ugly switches, but I'd rather avoid that unless it is actually required.

Perhaps?

---

### Post by suffring on 2021-10-27
Thank you.
In the meantime the HDMI dummy plug has arrived and works perfectly. I have had a look at your suggestion and the answer seems to be in there somewhere but may take a bit of trial and error for me - with my level of knowledge - to get to it. 
Thanks again and cheers

---

