---
title: "Firefox won't open links in new tabs, instead it opens them in a new window"
date: 2007-07-13
forum: General Help
---

### Post by moljac024 on 2007-07-13
Another issue that is Ubuntu related (didn't experience it with Fedora 7) is that firefox, for some reason, won't open links in new tabs.

What gives ? Can it be fixed ?

---

### Post by stalker145 on 2007-07-13
> **moljac024 said:**
> Another issue that is Ubuntu related (didn't experience it with Fedora 7) is that firefox, for some reason, won't open links in new tabs.

What gives ? Can it be fixed ?

There are two options to this: first is that you can change in the preferences (pretty sure) to have FireFox open in new tabs vice new windows, or second you can simply press the <ctrl> key while clicking the link (that's what I do).

Check back if this isn't what you mean or if it doesn't work.

---

### Post by orb9220 on 2007-07-13
Or middle-click mouse opens all links in new tabs for me.

---

### Post by rainwalker on 2007-07-13
Install the Tab Mix Plus extension, you can set it to do that and a lot of other things with it.

---

### Post by p_quarles on 2007-07-13
The "Tab Mix Plus" extension will give you a lot more configuration flexibility, including setting all links (or some) to open in new tabs. I've found it pretty useful.

EDIT: Rainwalker beat me to it :-)

---

### Post by stchman on 2007-07-13
> **moljac024 said:**
> Another issue that is Ubuntu related (didn't experience it with Fedora 7) is that firefox, for some reason, won't open links in new tabs.

What gives ? Can it be fixed ?

First off there needs to be a target="_blank" in the HTML code.  If there is then you need to do this:

Type about:config and set the variable browser.link.open_newwindow.  Give the parameter a value of 3.

This works.  Here are some more tweaks I have.  Some need to be updated.

[http://www.stchman.com/tweaks.html](http://www.stchman.com/tweaks.html)

---

### Post by rainwalker on 2007-07-13
The only thing I don't like about the Firefox that comes with Ubuntu is that it seems to mess up a little when handling CSS.

---

### Post by RangerDanger on 2007-07-17
> **moljac024 said:**
> Another issue that is Ubuntu related (didn't experience it with Fedora 7) is that firefox, for some reason, won't open links in new tabs.

What gives ? Can it be fixed ?

I know exactly what you mean and I hate this happening.  When I am browsing it is nice if the tabs just open like they do in Windows, they don't and it is easy to lose track of pages with all the open firefox windows than with tabs.  Also I have noticed firefox in Ubuntu does not auto select all text in the address field or search field and I have to manually delete when I want to do a new search or type a new address.

---

### Post by stalker145 on 2007-07-18
> **RangerDanger said:**
> Also I have noticed firefox in Ubuntu does not auto select all text in the address field or search field and I have to manually delete when I want to do a new search or type a new address.

I just double-click in the address/search field to select everything. Agreed that it was a tad annoying when I first discovered that issue, but here's your work-around ;)

---

### Post by 6StringKng on 2007-07-18
create a new tab, enter about:config in the url bar, hit enter, search for this "browser.link.open_newwindow" and change its value to 3 and should work...sorry if someone posted this, didn't want to read all of that, lmao.

---

### Post by moljac024 on 2007-07-20
Thanks for the responses guys (and/or gals)  :-D

I have installed tab mix plus and it's a great extension, one of the best! Don't know why it isn't in the recommended category on addons.mozilla.org....

---

