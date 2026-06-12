---
title: "Multiple Windows"
date: 2019-02-05
forum: General Help
---

### Post by angel mike on 2019-02-05
When I open up Firefox it gives me two blank windows instead of one. Is there a way of preventing this?

---

### Post by Claus7 on 2019-02-07
Hello,

usually more windows than one appear, if you have opened additional windows once, closed firefox or any other browser, and then they reopen again while relaunching the browser. If this is the case you should close these windows first and then close firefox and then relaunch it (if this fixes your issue). If not providing more info about your system and version of firefox might help as well as providing more info about what you did when you observed this issue.

Regards!

---

### Post by angel mike on 2019-02-24
On clicking on Firefox 65 I get two windows instead of a preferred single one.
On the Mozilla support page it suggests a solution for those running Microsoft Windows :

  	 	 	 	   "To help evaluate whether the Multiprocess (e10s) feature is causing problems, you could turn it off as follows:

 (1) In a new tab, type or paste **about:config** in the address bar and press Enter/Return. Click the button promising to be careful.
 (2) In the search box above the list, type or paste **autos** and pause while the list is filtered
 (3) Double-click the **browser.tabs.remote.autostart** preference to switch the value from true to false"

What would be the equivalent in Ubuntu? I cannot see anything in the Preferences on Firefox

---

### Post by angel mike on 2019-02-24
Thanks Claus7
Two windows appear when ever I launch Firefox ( the upto date version 65) from the basic desktop containing icons. See also my next post on the subject. I have Ubuntu 18.04.

---

### Post by Claus7 on 2019-02-26
Hello,

having read the other post of yours. I think that you could have them in one post. Concerning your issue. You can follow the same procedure in Firefox under linux. You do not go to preferences on Firefox, yet you go to the **address bar**, example: [www.ubuntu.com](www.ubuntu.com) . There, you erase everything and you type instead **about:config** and you press enter. If you follow the rest of the procedure you might be able to turn off the double windowed Firefox.

Regards!

---

### Post by coffeecat on 2019-02-26
> **Claus7 said:**
> 
having read the other post of yours. I think that you could have them in one post.

Agreed. @angel mike, please do not post duplicate threads about the same problem. This dilutes community effort and causes confusion. I've merged the two threads.

> **angel mike said:**
> 
On the Mozilla support page it suggests a solution for those running Microsoft Windows :

  	 	 	 	   "To help evaluate whether the Multiprocess (e10s) feature is causing problems, you could turn it off as follows:

 (1) In a new tab, type or paste **about:config** in the address bar and press Enter/Return. Click the button promising to be careful.
 (2) In the search box above the list, type or paste **autos** and pause while the list is filtered
 (3) Double-click the **browser.tabs.remote.autostart** preference to switch the value from true to false"

What would be the equivalent in Ubuntu? I cannot see anything in the Preferences on Firefox

Those instructions are not Windows specific. You do exactly the same in Ubuntu. Please also see Claus7's latest post which clarifies that for you.

---

