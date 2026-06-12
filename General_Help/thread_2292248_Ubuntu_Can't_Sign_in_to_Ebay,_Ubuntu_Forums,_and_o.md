---
title: "Ubuntu Can't Sign in to Ebay, Ubuntu Forums, and others - Secure Connection Failed"
date: 2015-08-26
forum: General Help
---

### Post by sheriff-pointing on 2015-08-26
Hi All,
I've got a mixture of Apple and Ubuntu machines on my home network.  None of the Ubuntu machines will sign in to Ebay, Ubuntu Forums and various other sites.  I can browse Ebay without logging in but when I try to sign in, the login page displays ok, I enter user and password, and after a minute or so of page loading, I get **"Secure Connection Failed"**.

I have a dual boot MacBook Pro which works fine running OSX, also Ubuntu VM works fine running over OSX host. If I reboot natively into Ubuntu, the problem returns.


[LIST]
[*]2 full time OSX machines and one dual-boot work fine running OSX
[*]2 full time Ubuntu Machines, and the dual-boot don't work running Ubuntu.
[*]Ubuntu VM's work fine running on an OSX host.
[/LIST]

Can anyone give me a pointer? I don't know where to start looking.

---

### Post by dino99 on 2015-08-26
i suppose your logs might be helpfull to narrow down the cause

[http://superuser.com/questions/826232/how-to-bypass-the-secure-connection-failed-warning-in-firefox-33](http://superuser.com/questions/826232/how-to-bypass-the-secure-connection-failed-warning-in-firefox-33)

---

### Post by sheriff-pointing on 2015-08-26
Thanks dino99,
I checked your link, I have a different problem, I should have mentioned that both firefox and chrome behave similarly.

Any hints as to which logs may contain helpful information?

---

### Post by sheriff-pointing on 2015-08-26
**Further information:  **Today I took my MacBook booted in to Ubuntu to the local university network.  Everything works fine on their network, so it seems the problem is related to how my home network interacts with Ubuntu.

Does anyone have any clue what settings could possibly be a problem?  Or as above, which logs to check?

---

### Post by sandyd on 2015-08-26
> **sheriff-pointing said:**
> Hi All,
I've got a mixture of Apple and Ubuntu machines on my home network.  None of the Ubuntu machines will sign in to Ebay, Ubuntu Forums and various other sites.  I can browse Ebay without logging in but when I try to sign in, the login page displays ok, I enter user and password, and after a minute or so of page loading, I get **"Secure Connection Failed"**.

I have a dual boot MacBook Pro which works fine running OSX, also Ubuntu VM works fine running over OSX host. If I reboot natively into Ubuntu, the problem returns.


[LIST]
[*]2 full time OSX machines and one dual-boot work fine running OSX
[*]2 full time Ubuntu Machines, and the dual-boot don't work running Ubuntu.
[*]Ubuntu VM's work fine running on an OSX host.
[/LIST]

Can anyone give me a pointer? I don't know where to start looking.
possibly issue with laptop date, can you post the output of
```

date
```

---

### Post by sheriff-pointing on 2015-08-27
Thanks for your help sandyd.
As follows:
```
me@linux-MacBookPro:~$ date
Thu Aug 27 18:17:34 AEST 2015
```

I don't understand what impact the date can have, could you possibly explain a little further?

---

### Post by sammiev on 2015-08-27
If your date is way off which it is not, certificates from a browser or website can see it as a possible secure issue.

---

### Post by sheriff-pointing on 2015-08-27
Thanks sammiev.

I swapped out my ADSL modem with one I had lying around and the problem went away.  I think my belkin ADSL modem was the problem.

EDIT: I swapped the original modem back in to service and "reset to factory defaults".  After putting all of my custom forwards etc back in to the modem everything was working.  It's odd, as no settings were changed for a long time (years).

---

