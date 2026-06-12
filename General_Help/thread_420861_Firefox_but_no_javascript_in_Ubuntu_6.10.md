---
title: "Firefox but no javascript in Ubuntu 6.10?"
date: 2007-04-24
forum: General Help
---

### Post by bwiese on 2007-04-24
To test my javascript, I go to this page: [http://segal.org/java/config/index.html](http://segal.org/java/config/index.html)
It reports "Javascript is not working" !?!?

I'm running Ubuntu 6.10, and haven't been able to get "javascript" working in Firefox.
I've never encounterend an error like this before. I removed all extensions, enabled javascript, actually uninstalled firefox (part of ubuntu-desktop) then reinstalled all of that stuff... still, no go.

Any insight into how javascript got broken on 6.10?
Any suggestions on what I should try next, other than a completely new Ubuntu install?

Brian

$ dpkg -l firefox
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name Version Description
+++-===============-===============-==============================================
ii firefox 2.0.0.3+0dfsg-0 lightweight web browser based on Mozilla

---

### Post by hanzomon4 on 2007-04-24
Try this - [Java *ubuntu wiki*]("https://help.ubuntu.com/community/Java")

---

### Post by bwiese on 2007-04-25
Thanks, but this is not a Java problem-- it's a Javascript problem.

Does anyone else have any suggestions?  I know it's an obscure problem, but I don't know why it is happening or how to fix it.  Javascript works fine in Epiphany and Galeon (thought it crashes easily).

Regards, Brian

---

### Post by bwiese on 2007-04-25
Ok,  I just found a solution... go to **about:config**
search for: **javascript.enabled**  

double clicked it to change it from FALSE to TRUE and javascript works again!

Going into Firefox Edit->Preferences, Content tab it now seems the Enable Javascript check box works, and effectively changes the setting in about:config as well.  This is great, probably the way it was intended to work, but for some reason it didn't earlier... I would have JS enabled in Preferences, but to luck according to that website.

OK, even ODDER YET - if I change the javascript.enabled setting from about:config and refresh the page... maps.google.com will respond properly (js enabled and maps work, js disabled and google maps redirects to straight html - [http://maps.google.com/?output=html)](http://maps.google.com/?output=html))... but [http://segal.org/java/config/index.html](http://segal.org/java/config/index.html) test page says that my "Javascript is not working" every time I refresh - when javascript is disabled AND enabled.  Perhaps it is saving state some how.  Oh well, I'm in business again.  Hope this helps someone else out in the future. =)

---

### Post by robbydek on 2007-04-27
I had the same javascript problem and the link provided by ]hanzomon4 worked.  I used the "Selecting the default Java version" area and followed the instructions listed.  I restarted the browser and java had finally installed correctly after giving me so much trouble.

---

