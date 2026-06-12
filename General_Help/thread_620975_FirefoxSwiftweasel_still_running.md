---
title: "Firefox/Swiftweasel still running"
date: 2007-11-23
forum: General Help
---

### Post by mwdowns on 2007-11-23
Hello folks :)

I have a dual boot of Windows and Ubuntu.  I spend a good deal of time in the Windows environment, but boot into Ubuntu when I'm not in the gaming mood.  ;)  However, when I boot into Ubuntu and click on the Swiftweasle icon I get an error message saying that Swiftweasle is already running and that I must shut it down in order to start a new session.  The same thing happens with Firefox.  When I look in the System Monitor, neither Firefox nor Swiftweasle is running.  What should I do?

I have recently copied one of my Firefox profiles from my Windows partition into my Ubuntu home partition.  Is that a problem?

Let me know if you need any more info.

Thanks for your help.

---

### Post by Forlong on 2007-11-23
> **mwdowns said:**
> I have recently copied one of my Firefox profiles from my Windows partition into my Ubuntu home partition.  Is that a problem?
Indeed. Open **~/.mozilla/firefox/profiles.ini** and make sure you are using the proper path to the profile you want to use.

---

