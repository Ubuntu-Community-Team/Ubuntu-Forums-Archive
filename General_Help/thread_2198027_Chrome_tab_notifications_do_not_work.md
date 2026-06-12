---
title: "Chrome tab notifications do not work"
date: 2014-01-06
forum: General Help
---

### Post by childintime on 2014-01-06
[COLOR=#333333][FONT=UbuntuRegular]Hello :)
As you probably now in Windows when using Chrome and you get email in Gmail or you get Facebook notification, then that tab has highlighted moving effect so you can see you get new notification.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]But since I installed Ubuntu 13.10 this does not work, and I couldn't find how to do it. Any idea how to make it work again?[/FONT][/COLOR]

---

### Post by bapoumba on 2014-01-06
I do not know about Windows, but I never got that on Ubuntu. The tab has a little number that shows up when I get a new email in gmal for ex, but not any effect.
You should check the notification settings under both gmail (settings > general) and FB (I do not have it open, guess you can find it ;)).

---

### Post by childintime on 2014-01-07
> **bapoumba said:**
> I do not know about Windows, but I never got that on Ubuntu. The tab has a little number that shows up when I get a new email in gmal for ex, but not any effect.
You should check the notification settings under both gmail (settings > general) and FB (I do not have it open, guess you can find it ;)).

Okay I enabled some notification in gmail and now I get a pop up when email arrives. It's good, but still pop up disappears after few seconds and if I am not at computer I won't see it. For FB I got everything enabled, but nothing appears on the tab itself :)

---

### Post by bapoumba on 2014-01-07
Hmm. In Chrome > Settings > Privacy > Content settings, there is an item for notifications.
Other than that, I've ran out of ideas (and did not find anything interesting).

---

### Post by childintime on 2014-01-08
> **bapoumba said:**
> Hmm. In Chrome > Settings > Privacy > Content settings, there is an item for notifications.
Other than that, I've ran out of ideas (and did not find anything interesting).

Thank you sir. I enabled that as well (was disabled before) but no difference, no notification that I get new event in FB or gmail, apart from gmail pop-up.

---

### Post by bapoumba on 2014-01-13
Please try with the pinned tab feature. Right click on the tab (gmail for ex) and pin it. You can undo by right click and unpin. Once done, all the pinned tabs will be on the left with only their logo on it. Any new tab opened will be place right of all pinned tabs. As the number of unread new content is not shown on pinned tabs, they should flicker to show notifications. Trying it right now, waiting for some new mail to see if it woks :)

Edit : it works. The tab is highlighted and flickers but does not move or bounce.

---

### Post by childintime on 2014-01-14
> **bapoumba said:**
> Please try with the pinned tab feature. Right click on the tab (gmail for ex) and pin it. You can undo by right click and unpin. Once done, all the pinned tabs will be on the left with only their logo on it. Any new tab opened will be place right of all pinned tabs. As the number of unread new content is not shown on pinned tabs, they should flicker to show notifications. Trying it right now, waiting for some new mail to see if it woks :)

Edit : it works. The tab is highlighted and flickers but does not move or bounce.

Really? :o I always have some of the tabs pinned in Chrome, like Gmail, but they never flicker or do any kind of animation when new notification comes. That only worked on Windows for me, but since I installed Ubuntu it's gone.

---

### Post by bapoumba on 2014-01-14
Chromium Version 31.0.1650.63 Ubuntu 13.10 (31.0.1650.63-0ubuntu0.13.10.1~20131204.1) here.
One more thing, the tab stays pinned after closing and reopening the browser, or after a reboot.

---

### Post by childintime on 2014-01-14
> **bapoumba said:**
> Chromium Version 31.0.1650.63 Ubuntu 13.10 (31.0.1650.63-0ubuntu0.13.10.1~20131204.1) here.
One more thing, the tab stays pinned after closing and reopening the browser, or after a reboot.

[COLOR=#303942][FONT=Ubuntu]Chrome version 31.0.1650.63, Ubuntu 13.10

And yep, it always stays pinned, that's the whole point :)[/FONT][/COLOR]

---

### Post by bapoumba on 2014-01-14
> **sladeinflame7 said:**
> [COLOR=#303942][FONT=Ubuntu]Chrome version 31.0.1650.63, Ubuntu 13.10

And yep, it always stays pinned, that's the whole point :)[/FONT][/COLOR]

Well, yes, but looking around the internetz about your question, I saw there were discussions regarding the tab not staying pinned for some. I'm quite surprised it works here and not for you. Do you allow javascript ?

---

### Post by childintime on 2014-01-14
> **bapoumba said:**
> Well, yes, but looking around the internetz about your question, I saw there were discussions regarding the tab not staying pinned for some. I'm quite surprised it works here and not for you. Do you allow javascript ?

Yes sir. "Allow all sites to run JavaScript" is checked in Chrome.

---

### Post by bapoumba on 2014-01-14
Maybe have a look at your extensions then, and temp disable them one by one to see if one is messing around. Or make a new profile in Chrome where you do not add any extension.

---

### Post by childintime on 2014-01-14
> **bapoumba said:**
> Maybe have a look at your extensions then, and temp disable them one by one to see if one is messing around. Or make a new profile in Chrome where you do not add any extension.

All extensions disabled, still nothing :(

---

### Post by bapoumba on 2014-01-14
Hmm, I'm kind of running out of ideas again. Are you using a standard theme ?

---

### Post by childintime on 2014-01-14
> **bapoumba said:**
> Hmm, I'm kind of running out of ideas again. Are you using a standard theme ?

I don't know which theme I used tbh, I don't remember changing it actually. Anyways, tried Classic theme, nothing and then tried GTK+ theme in settings and I finally got blinking effect on receiving email! It's different than it was in Windows, but that was few months ago so maybe they changed it. I tried few other custom themes and blinking works well.

Thanks for helping me bapoumba ;)

---

### Post by bapoumba on 2014-01-14
> **sladeinflame7 said:**
> I don't know which theme I used tbh, I don't remember changing it actually. Anyways, tried Classic theme, nothing and then tried GTK+ theme in settings and I finally got blinking effect on receiving email! It's different than it was in Windows, but that was few months ago so maybe they changed it. I tried few other custom themes and blinking works well.

Thanks for helping me bapoumba ;)

So I'm going to make your tab blink once more : if your issue is solved, please mark it as such from the "Thread Tools" menu, thanks!
And you are very welcome :)

---

### Post by childintime on 2014-01-14
Yes, done.

P.S. All the time I was talking about pinned tabs, but for some reason I forgot to mention it from the beginning :P

---

### Post by bapoumba on 2014-01-14
> **sladeinflame7 said:**
> Yes, done.

P.S. All the time I was talking about pinned tabs, but for some reason I forgot to mention it from the beginning :P
And I should thank you for that. I had no idea it existed, found it looking around for you, and now I'm using it ;)

---

### Post by childintime on 2014-01-14
> **bapoumba said:**
> And I should thank you for that. I had no idea it existed, found it looking around for you, and now I'm using it ;)

Glad to hear, it's really nice feature :)

---

