---
title: "Increase chrome scrolling speed"
date: 2012-11-06
forum: General Help
---

### Post by Pashok on 2012-11-06
I've tried to search for a way doing this, but nothing seemed to help, i use ubuntu 12.10.

When i had ubuntu 11.10 the following worked for me:
google-chrome --scroll-pixels=150.

The default scrolling is too slow and unusable for me.

Thanks!

---

### Post by speedwell68 on 2012-11-06
Is there not an addon that allows you to adjust the scroll speed available in the Chrome Web Store?

---

### Post by Pashok on 2012-11-14
If you know any, please share.

---

### Post by Pashok on 2012-11-16
bump

---

### Post by bman on 2013-01-26
I have the same problem. Ubuntu 12.04

How do I change the speed? I do not want to use that extension, I used it before but it caused more problems then it fixed.

---

### Post by gifford on 2013-01-26
I use the extension Smooth Scrollerator and it works well. Also under chrome://flags you can enable smooth scrolling to see if it helps.

---

### Post by bman on 2013-01-26
I didn't want to use an extension because of the one I did try. Caused too many problems.

That one seems to work quite well though.

Thanks

---

### Post by Paper Bag on 2013-02-27
*--scroll-pixels* has been removed from Chrome 25.x (recently became stable, Chromium revision [here]("http://src.chromium.org/viewvc/chrome?view=rev&revision=167590")). Explanation:

> As stated there, UI isn't going to be added to the settings page to make this configurable, and this command-line flag was only added for Chrome OS touchpads and was not intended to be maintained indefinitely.
[https://code.google.com/p/chromium/issues/detail?id=154776](https://code.google.com/p/chromium/issues/detail?id=154776)

I'm pissed because this greatly reduces the usability, but rather than blame the Chromium devs, I'd like to blame GNOME for not having such simple system wide setting in the first place. And the way the GNOME is dumbing down and hiding settings, it doesn't look like this would be a high priority in the future either. Back to good old PgUp/Down scrolling then.

Also, please star this issue: [https://code.google.com/p/chromium/issues/detail?id=167197](https://code.google.com/p/chromium/issues/detail?id=167197)

---

### Post by Paper Bag on 2013-09-21
Extension for Chrome: [https://chrome.google.com/webstore/detail/chromium-wheel-smooth-scr/khpcanbeojalbkpgpmjpdkjnkfcgfkhb](https://chrome.google.com/webstore/detail/chromium-wheel-smooth-scr/khpcanbeojalbkpgpmjpdkjnkfcgfkhb)

Unfortunately this forces smooth scrolling to be on (as the extension name suggests). Otherwise it works and you can really change the "scrolls n lines" setting.

Btw,
[URL="https://bugzilla.gnome.org/show_bug.cgi?id=692666"]
https://bugzilla.gnome.org/show_bug.cgi?id=692666[/URL]
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/124440](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/124440)

The fact that you still can't set this OS-wise is a perfect answer to the question "is Linux ready for mainstream".

---

