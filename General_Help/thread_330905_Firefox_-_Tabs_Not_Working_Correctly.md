---
title: "Firefox - Tabs Not Working Correctly"
date: 2007-01-03
forum: General Help
---

### Post by BarfBag on 2007-01-03
I use Firefox 2.0 in both Windows and Ubuntu.  In Windows, when I click a link that's suppost to open a new window, it opens in a new tab.  This doesn't happen in Ubuntu.  I have to click it with the scroll wheel.  The settings are exactly the same.  How do I fix this?  It's really getting on my nerves.

---

### Post by bruenig on 2007-01-03
> **BarfBag said:**
> I use Firefox 2.0 in both Windows and Ubuntu.  In Windows, when I click a link that's suppost to open a new window, it opens in a new tab.  This doesn't happen in Ubuntu.  I have to click it with the scroll wheel.  The settings are exactly the same.  How do I fix this?  It's really getting on my nerves.

Edit>Preferences, make them open in tabs.

---

### Post by Raptor45 on 2007-01-03
I've noticed the same thing. Bugs me too.

EDIT: I've got it set to open in tabs, but on some links it'll still do a window.

---

### Post by BarfBag on 2007-01-03
> **bruenig said:**
> Edit>Preferences, make them open in tabs.

It's set to that.  It doesn't work.  The preferences are identical to the ones in Windows.

---

### Post by bruenig on 2007-01-03
Perhaps you should get some of the tab extensions like tab mix plus or tabbrowser preferences.

---

### Post by NT4usB on 2007-01-03
Type in the browser window.:
```
about:config
```

Type in the search window.:
```
browser.link.open
```
 You should get three results.
(double click to) Set:
browser.link.open_external = 3 
browser.link.open_newwindow = 3 
browser.link.open_newwindow.restriction = 2

ed: Oops. Just reread your post.
This will make everything open in a tab/new tab. **no** extra windows.
But you can tweak them (0-3) in one tab and load stuff in another to see how they affect opening in tabs/windows.
More reading:

[http://kb.mozillazine.org/Browser.link.open_external](http://kb.mozillazine.org/Browser.link.open_external)
[http://kb.mozillazine.org/Browser.link.open_newwindow.restriction](http://kb.mozillazine.org/Browser.link.open_newwindow.restriction)

---

### Post by Raptor45 on 2007-01-03
Why would it be altered from the defaults?

---

