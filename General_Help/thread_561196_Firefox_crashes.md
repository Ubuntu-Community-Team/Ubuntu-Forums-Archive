---
title: "Firefox crashes"
date: 2007-09-27
forum: General Help
---

### Post by VHans on 2007-09-27
Hello,
Since this morning Firefox crashes every time when I navigate to my home-banking site. Before today I had no problems at all with this site. I tried with Epiphany and the problem is the same.
The site uses Java, maybe something is wrong with the plugin.

I use Ubuntu 7.04, Java Plug-in 1.6.0-b105, Firefox 2.0.0.6. This morning there was an update for update manager which I installed. Could this have something to do with the problem?
Hans

---

### Post by madoracle on 2007-09-27
It could be one of several problems, but some research indicates its most likely one of two things:

Bad java coding on your bank's part or, more likely, one of your plugins for Firefox not related to java is causing excess memory to be used. One plugin that is supposed to monitor memory usage in firefox is located here: [http://dbaron.org/mozilla/leak-monitor/](http://dbaron.org/mozilla/leak-monitor/)

Have you installed any new addons recently that might be the culprit? 
Also have you tried it with a different OS entirely?

Actually since you mentioned it happened with a different browser, I'd say the problem is most likely with your bank's coding. Try it on Windows using IE, often companies refuse to write code that'll work with Firefox. Another thing - try upgrading to Firefox 2.0.0.7. It fixed several bugs, including a gaping security hole.

---

### Post by VHans on 2007-09-28
Madoracle, thanks for your reply. I am still waiting for a reply from the bank before trying the other solutions. I don't think that updating Firefox will help because I have the same problem with Epiphany. If all else fails I will do so anyway (or 2.0.0.7 will come automatically with the Ubuntu updates).

Hans

---

