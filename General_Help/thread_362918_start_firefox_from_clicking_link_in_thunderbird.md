---
title: "start firefox from clicking link in thunderbird"
date: 2007-02-16
forum: General Help
---

### Post by AGSzabo on 2007-02-16
when i click a link in my email (thunderbird) and firefox is running, the link is opened in firefox. but if firefox is not running, nothing happens! how can i let firefox auto start when a link is clicked in thunderbird?

---

### Post by louis_nichols on 2007-02-16
hm... is firefox set as the default browser? this is done under System>Preferences>Default applications

---

### Post by AGSzabo on 2007-02-18
yes, firefox is default browser. and the command looks:

firefox -remote "openurl(%s,new-tab)"

---

### Post by louis_nichols on 2007-02-18
OK. You need to change that setting from "Open link in new tab" to "Open link in web browser default". If you want to not replace the page on the active tab in Firefox when clicking a link in Thunderbird, use a firefox extension that lets you set it to always redirect external links to new tabs. *Tab mix plus* is the one I use for this and recommend.

---

### Post by aysiu on 2007-02-18
Read this thread:
[Clicking on links in Thunderbird and having them open in Firefox [Resolved]](http://ubuntuforums.org/showthread.php?t=60427)

---

### Post by AGSzabo on 2007-02-18
the change to "Open link in web browser default" did it all. firefox starts and if it is already startes then a new link obens in a tab. i wonder a little because i couldnt find an extension insatlled.
thank you

---

### Post by louis_nichols on 2007-02-18
> **AGSzabo said:**
> the change to "Open link in web browser default" did it all. firefox starts and if it is already startes then a new link obens in a tab. i wonder a little because i couldnt find an extension insatlled.
thank you

It may just be the default setting. I wouldn't know, cause I've had this extension since I don't even remember when anymore. :) I think it may have been even the FF 1.0.x era. Anyways, I set it to always open new tabs when links are requested from outside FF

---

