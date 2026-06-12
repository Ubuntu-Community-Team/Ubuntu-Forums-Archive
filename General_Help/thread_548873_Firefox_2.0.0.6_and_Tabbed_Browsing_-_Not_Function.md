---
title: "Firefox 2.0.0.6 and Tabbed Browsing - Not Functioning Properly"
date: 2007-09-11
forum: General Help
---

### Post by tallthom on 2007-09-11
Using Ubuntu 7.04 with Firefox 2.0.0.6.

I have the Firefox options under tabbed browsing set to **open new links in a new tab** (not a new window) yet many links open a new window.  Anyone else seeing this behavior?:confused:

Workaround is to always right-click and select "open in new tab", but that negates convenience of the setting in the options.  :(

I'm kind of new, so if there is a place to log a bug for this thing maybe someone could point me in the right direction.  Or if there is something else I need to change in the settings, they could help me out?

Also, could the moderator of the list help me move this thread to the right forum?  I'm not certain this is the right place to put it.

---

### Post by chameleonkid on 2007-09-11
I'm having the same problem! And was wondering why this is happening. On a side note,  I am using the restricted driver w/o desktop effects enabled. When they were enabled opening a new tab would 75% of the time Crash my system. Took off the effects and now its a little better but still crashes occasionally. Digg is the worst though, opening a new tab to metacafe is absolutely dreadful.

---

### Post by kostkon on 2007-09-12
Install the *Tab Mix Plus* Firefox extension (from mozilla.com) and you will be able to solve this problem. With this extension you will get many more options to define the behavior of your tabs in general.

---

### Post by tallthom on 2007-09-12
Thanks for the feedback.

I'll try the browser add-on, but this seems like another workaround.  Would people agree that this behavior is indeed a defect and should be logged as such?

Just curious about the defect/bug reporting process, I guess.

---

### Post by kostkon on 2007-09-12
I don't think it's *Ubuntu*'s bug, of course, nor *Firefox*'s. It's just that by its default behavior, *Firefox* is not able to catch all the new window links from web pages. Like the ones that use the *target="_blank"* *HTML* attribute that many pages use, even with javastript tricks, in order to trick you and show, for example, the ads they want you to see by force in a new window!

With the extension you'll add more functionality to *Firefox*, and it should be able to open all the new window *signals* to new tabs.

That's why the extensions for Firefox exist, after all!

---

### Post by noynac on 2007-09-12
--please delete--

---

### Post by tallthom on 2007-09-12
Thanks for the help.  I tried that add-on and it works great.  This post is closed!

---

### Post by chameleonkid on 2007-09-12
I tried going back and changing it to window then back to tabbed again. And it seemed to work. But I also hopped over to KDE (doubt that makes a difference).

---

### Post by nick_h on 2007-09-13
This is a known problem with Firefox.  You have found the workaround - simply change back to opening in a window and then back to opening in a tab again.

---

### Post by stchman on 2007-09-13
> **tallthom said:**
> Using Ubuntu 7.04 with Firefox 2.0.0.6.

I have the Firefox options under tabbed browsing set to **open new links in a new tab** (not a new window) yet many links open a new window.  Anyone else seeing this behavior?:confused:

Workaround is to always right-click and select "open in new tab", but that negates convenience of the setting in the options.  :(

I'm kind of new, so if there is a place to log a bug for this thing maybe someone could point me in the right direction.  Or if there is something else I need to change in the settings, they could help me out?

Also, could the moderator of the list help me move this thread to the right forum?  I'm not certain this is the right place to put it.

Very easy fix.

Type about:config in the URL place.  Search for browser.link.open_newwindow and give it a value of 3.  This will cause a new window to open when the target="_blank" is used in HTML.  I agree that it should be set to 3 by default.

Here are some other tweaks.

[http://www.stchman.com/tweaks.html](http://www.stchman.com/tweaks.html)

---

### Post by otterstrom on 2007-09-16
Thanks, I had the same problem and it was fixed by switching the preferences to "open in new window" and then back to "open in new tab".

---

