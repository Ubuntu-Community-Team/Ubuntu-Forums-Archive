---
title: "X2go Server and Client working.  X2go Server Web Browser problem."
date: 2016-08-27
forum: General Help
---

### Post by madhartigan on 2016-08-27
I have had no problem getting my x2go server and client to communicate and I'm able to access the xfce desktop on the x2go server from my Windows PC without a problem.

My problem is that when I try to load the xfce Web Browser it appears to connect to nothing.

This is what I see when I click the "Web Browser" launcher button:

[ATTACH=CONFIG]270902[/ATTACH]


Not sure what it's trying to load there, but my guess is that the launcher needs a proper browser to launch.

Looking at the launcher properties for that icon, I can see that it's calling a "web browser", which I don't have installed.

[ATTACH=CONFIG]270901[/ATTACH]


My questions is how to I provide the launcher a browser to install?  I've never used x2go prior to this and since there is no apparent package manager to use for installing browsers, I'm not sure how to proceed?

Do I just use apt-get from the command line and install any browser I choose or is there a specific method that ensures xfce sees the browser I've installed and associates it with that "Web Browser" launcher icon?


Any help would be appreciated.  I'm hesitant to just experiment.

---

### Post by TheFu on 2016-08-27
Yes, use APT, just like it was a real Ubuntu install - er ... because it is. The only difference is that you are using a remote desktop. That alters the ability to run some GPU-dependent programs, but nothing else.

To fix the default browser, there is a properties app somewhere - check the menu for it - set the full path to whatever browser you install there.

---

### Post by madhartigan on 2016-08-31
Thank you very much for the reply.  Sorry I haven't been back sooner.  Start of classes and such delayed my ability to work on the problem.  I'll give apt a shot and should have no problem properly fixing the default browser.

Definitely appreciate the time you took to provide your suggestions.

Add:  It worked flawlessly, as I'm sure you expected.  Thanks again.

---

