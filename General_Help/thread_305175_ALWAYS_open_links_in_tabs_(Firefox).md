---
title: "ALWAYS open links in tabs (Firefox)"
date: 2006-11-22
forum: General Help
---

### Post by brottman on 2006-11-22
How can I make Firefox (in Edgy) always, ALWAYS open links in a tab? Pisses me off every time Firefox spawns a new FF window.

---

### Post by ravenon on 2006-11-22
Go to Edit Preferences Tabs

---

### Post by TheRingmaster on 2006-11-22
my swiftfox still opens in the current window even though I am telling it to open in a new tab. what is up with this?

---

### Post by hellfried on 2006-11-26
> **ravenon said:**
> Go to Edit Preferences Tabs

having the same problem as the first poster despite selecting the option for 'new tab'. any ideas?

---

### Post by jincast90 on 2006-11-26
> **hellfried said:**
> having the same problem as the first poster despite selecting the option for 'new tab'. any ideas?

I have the solution for you. Download the extension TabMixPlus. Then configure it to open links in new tab instead of window.

---

### Post by mayonaise15 on 2006-11-26
I just fixed this myself

Open a new window or tab and type about:config in to the address bar.
In the filter section type browser.link

It should have 3 options you can change.  This is how I have mine set:
browser.link.open_external                 3
browser.link.open_newwindow                3
browser.link.open_newwindow.restriction    0

And if you do need to open a link in a new window, you can shift-click the link for that.

---

### Post by hellfried on 2006-11-26
> **jincast90 said:**
> I have the solution for you. Download the extension TabMixPlus. Then configure it to open links in new tab instead of window.

thanks its working great!

---

### Post by marcantonio on 2006-11-27
> **mayonaise15 said:**
> I just fixed this myself

Open a new window or tab and type about:config in to the address bar.
In the filter section type browser.link

It should have 3 options you can change.  This is how I have mine set:
browser.link.open_external                 3
browser.link.open_newwindow                3
browser.link.open_newwindow.restriction    0

And if you do need to open a link in a new window, you can shift-click the link for that.

Had the same problem.  Mine is set to:

browser.link.open_external 3
browser.link.open_newwindow 3
browser.link.open_newwindow.restriction **2**

Check [here]("http://kb.mozillazine.org/Browser.link.open_newwindow.restriction") and [here]("http://kb.mozillazine.org/Browser.link.open_external") for more info.

---

### Post by jincast90 on 2006-11-27
> **hellfried said:**
> thanks its working great!

Sure thing. I remember how much I hated it myself undtil I found out about TabMixPlus 8)

---

### Post by astromech on 2007-12-16
> **mayonaise15 said:**
> I just fixed this myself

Open a new window or tab and type about:config in to the address bar.
In the filter section type browser.link

It should have 3 options you can change.  This is how I have mine set:
browser.link.open_external                 3
browser.link.open_newwindow                3
browser.link.open_newwindow.restriction    0

And if you do need to open a link in a new window, you can shift-click the link for that.

Thank you! It works now ! :)

---

### Post by blaineT on 2008-06-20
> **mayonaise15 said:**
> I just fixed this myself

Open a new window or tab and type about:config in to the address bar.
In the filter section type browser.link

It should have 3 options you can change.  This is how I have mine set:
browser.link.open_external                 3
browser.link.open_newwindow                3
browser.link.open_newwindow.restriction    0

And if you do need to open a link in a new window, you can shift-click the link for that.

Thanks so much for this, took a decent amount of searching and confusion after reading available descriptions for browser.link.open_newwindow.restriction before I found this post. Solved the problem for me instantly (FF 3.0).

---

