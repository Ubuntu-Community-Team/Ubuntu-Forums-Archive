---
title: "[SOLVED] Firefox 2.0.0.11 Chrome Conflict"
date: 2007-12-06
forum: General Help
---

### Post by Gilgad Drumheller on 2007-12-06
Using Gutsy (7.10)
Most recent update to Firefox seems to have created problems within the chrome files used for certain parts of the user interface.  For instance:
*Prefrences window doesn't open
*Addons window pops up with: 
```
XML Parsing Error: syntax error
Location: chrome://mozapps/content/extensions/extensions.xul
Line Number 1, Column 1:box-align: center;
^
```
*History sidebar makes sidebar with:
```
XML Parsing Error: not well-formed
Location: chrome://browser/content/history/history-panel.xul
Line Number 1, Column 1:/ screen.height;
^
```

While updating i had a custom firefox theme applied (Macfox Graphite, relatively popular)
I tried uninstalling and reinstalling (complete), but it still starts with my previous theme.  I have also attempted removing the ~/.mozilla directory, and the /usr/share/firefox directory, but no luck.

Is there any good way to restore factory settings?

---

### Post by Gilgad Drumheller on 2007-12-06
I realize that this is probably wasteful, but i'm leaving this up here for anyone who runs into similar problems.
All I had to do was restart my machine, and everything worked.

Heres the breakdown of what i think happened:
Some of the things i ran across while trying to solve this problem mentioned running firefox  as "firefox -a asdf", which starts a completely new instance of firefox with the application identification "asdf".  Apparently some part of firefox is left running even after the browser window closes.  This was refering to files that didn't exist, especially after I deleted the profile folder.  Restarting the computer reset the firefox backend, so now everything is good.

---

### Post by solbot on 2008-02-09
Even faster than rebooting is to open the System Monitor and just kill all firefox-bin processes.
Then reopen Firefox and it *should* work.

---

