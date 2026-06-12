---
title: "Firefox 3 not working"
date: 2008-05-30
forum: General Help
---

### Post by getfirefox on 2008-05-30
Every time I try to open Firefox a box pops up and says: 

'TypeError: bookmarkContextItem is nul' 

and another says: 

"XML Parsing Error: undefined entity
Location: chrome://browser/content/browser.xul
Line Number 242, Column 5:    <key                          key="&fullZoomReduceCmd.commandkey2;"  command="cmd_fullZoomReduce"  modifiers="accel"/>
----^"

I have tried typeing this into terminal:

apt-get purge firefox-3.0

rm /usr/lib/firefox*

rm /etc/firefox*

apt-get install firefox-3.0

and it still happens. I am currently using minefield. Please help :( Thanks.

---

### Post by Bakon Jarser on 2008-05-30
looks like when you uninstalled you got everything but the .mozilla in your home folder.  try deleting that and then reinstalling firefox.

---

### Post by getfirefox on 2008-05-30
Thanks! Its working now xD.

---

