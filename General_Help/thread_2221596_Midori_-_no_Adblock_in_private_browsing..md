---
title: "Midori - no Adblock in private browsing."
date: 2014-05-02
forum: General Help
---

### Post by Elastic_Potential on 2014-05-02
I noticed this the other day, and I'm not sure if this is an unreported bug with Midori or if it's just some misconfiguration on my end.  Does this happen for anyone else?

---

### Post by vasa1 on 2014-05-02
If you don't get an answer here, try [https://answers.launchpad.net/midori](https://answers.launchpad.net/midori)
Midori's dev hangs out there. And there's IRC as well:
> Join #midori on irc.freenode.net for discussions about bugs and development.

---

### Post by Elastic_Potential on 2014-05-02
The midori irc channel seems dead, but I've filed a report on Launchpad.  I'll report back with my findings if anything meaningful arises.

---

### Post by Elastic_Potential on 2014-05-21
Well, I don't know how this didn't show up in dozens upon dozens of searches.  But, in trying to discover where Midori stores its cookies, [I found a useful tidbit of information](http://midori-browser.org/faqs/):
> 
A private window is a separate process, so crashes don't affect the normal browser session. No sensitive data such as cookies, history or bookmarks are stored. **No extensions are loaded.** Panels are not available.


So, it looks like it isn't a bug, but I can't understand how the developers reason that disabling the adblocker of all things is a good idea.  Alas.

Solved.

---

