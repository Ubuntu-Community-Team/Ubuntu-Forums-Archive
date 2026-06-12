---
title: "Firefox Tabs"
date: 2007-04-09
forum: General Help
---

### Post by Petester on 2007-04-09
I used to use only tabs but not windows in FF Windows, however in ubuntu i couldnt get it to work. Ex. When i click a link in google it opens in a new window instead of tab. 

I have already set "Open new webpage in a new tab" in FF preferences but it doesnt work..

Can anyone help? Thanks

---

### Post by laidback on 2007-04-09
I find that sometimes they open automatically and sometimes not. Cntrl+T to open your own tabs.

I have "Force link that open a new window to open a new tab" selected in preferences>tabs.
Played with all the options but have never got it to work exactly the way I expected. But generaly it's good, seems to depend on the site visited.

---

### Post by Petester on 2007-04-09
I dont see that option in settings.... would uninstalling ff and then download again work?

---

### Post by LeslieL on 2007-04-09
Firefox 1.5 used to behave nicely, always opening links in a new tab like I'd told it to. When I upgraded to 2.0 it started ignoring that instruction.The same problem is being discussed [here.]("http://ubuntuforums.org/showthread.php?p=2424751#post2424751") It may be a bug. One person in that thread suggests setting new pages to open in a new window and then switching back to the new tab opt&#305;on. I'm about to try that.

---

### Post by liljoe76 on 2007-04-09
Tabbrowser Preferences
[http://216.55.161.203/theonekea/tabprefs/](http://216.55.161.203/theonekea/tabprefs/)
Tab Clicking Options
[http://twanno.mozdev.org/](http://twanno.mozdev.org/)
both have been in my extensions list 3 odd years. i have everything open in tabs via TB prefs + mouseover brings tab up. TC options is set to close tab on double click.

---

### Post by laidback on 2007-04-09
It's Edit>Preferences>tabs to see the options I referred to.

---

### Post by fujikofujio on 2007-04-13
I had the same problem, even though I selected the option to open new windows in tabs it still kept on opening them in new windows. This option worked so well in windows, why fail on linux now??? 

Anyways the tabbrowser preferences fixed this issue, but I still think you shouldn't have to install another extension for something that is supposed to be an option.

---

### Post by daz23 on 2007-04-21
You don't need an extension for this. Type  about:config in the address bar. Search for browser.link.open_newwindow. Double-click on it to modify and give it a value of 3.  

[http://kb.mozillazine.org/Browser.link.open_newwindow.restriction](http://kb.mozillazine.org/Browser.link.open_newwindow.restriction)

---

