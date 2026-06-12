---
title: "firefox 2.0.0.2 tab problem [Resolved]"
date: 2007-03-04
forum: General Help
---

### Post by nflp1999 on 2007-03-04
I hate to post this stupid problem since I know it's gotta be something I'm doing that is gonna be real easy to fix but here goes.
   I am using firefox 2.0.0.2 and everything works fine...except the tabs.  I can do the tabs just fine but when I click a link it opens a new window instead of putting that link in a new tab.  I went under preferences and told it to open links in a new tab, not a new window, but ignores that and opens them in a new window instead.  What am I missing to get new links in new tabs??:confused:

---

### Post by Tantalus90 on 2007-03-04
You sure you dont have more than one window open when going in to the settings ?

It will take the settings from last closed window and save them for the next session

Hope that helps

---

### Post by berserker on 2007-03-04
Do you have Tab Mix Plus or some other tab extension installed?  If so then you will have to adjust the preferences in the extension as well.

HTH

---

### Post by aysiu on 2007-03-04
I, too, would recommend the Tab Mix Plus extension.

You can have "new window" events open up in new tabs (marked in red), or you can also enable "single window mode" (marked in green) to have **everything** forced into one window (with multiple tabs).

---

### Post by nflp1999 on 2007-03-04
perfect!  The Tab Mix Plus plugin worked like a charm.  Thanks!

---

### Post by Kheops_74 on 2007-03-05
I had the same problem. Sometimes links was open in a new window instead of a tab. In about:config ([http://kb.mozillazine.org/Firefox_:_FAQs_:_About:config_Entries](http://kb.mozillazine.org/Firefox_:_FAQs_:_About:config_Entries)) i put in the field open_newwindow.restriction ([http://kb.mozillazine.org/Browser.link.open_newwindow.restriction](http://kb.mozillazine.org/Browser.link.open_newwindow.restriction)) the value 0. 

It works for me.

Bye

---

