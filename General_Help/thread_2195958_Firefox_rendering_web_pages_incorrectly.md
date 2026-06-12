---
title: "Firefox rendering web pages incorrectly"
date: 2013-12-27
forum: General Help
---

### Post by t0p on 2013-12-27
A few days ago Firefox started acting up, rendering some sites incorrectly.  Have a look at the attached screenshots.  'Screenshot from 2013-12-27 13:12:33.jpg' is how Firefox is displaying a page from theguardian.com, and 'Screenshot from 2013-12-27 13:18:57.jpg' is how Chromium is (correctly) displaying the same page.

I've been having internet connection speed issues lately.  Is that somehow the cause of the display issues?  I know switching to Chromium full-time would be a solution.  But I've been using Firefox for years and would prefer to stick with it.  So, is there a solution to this rendering problem that doesn't involve switching browser?

Cheers.

---

### Post by Elfy on 2013-12-27
I'd be looking at your addons before changing browser.

Using ff here I see what you see with chromium.

---

### Post by The Cog on 2013-12-27
I just tried that page in firefox (v26.0) and it renders OK here. It looks to me as though you might be missing a style sheet, which could be caused by network problems - the stylesheed would be a separate download. Does the page render any better if you reaload it?

Another possibility is that there is something in your firefox settings that's causing issues. Try logging in as guest and using firefox there, or (while firefox is not running) temporarily renaming your ~/.mozilla folder to hide your normal settings from it.

---

### Post by t0p on 2013-12-28
The problem is erratic.  It seems to happen when the connection speed is low, which may be down to the stylesheets as mentioned by The Cog. If/when it raises its ugly face again I will try disabling add-ons.  Thanks for all responses.

---

