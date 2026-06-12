---
title: "Problem with Chromium Web Apps"
date: 2017-08-07
forum: General Help
---

### Post by Iggy64 on 2017-08-07
[SIZE=2][FONT=arial]I regularly create desktop shortcuts to web apps using the Chromium browser.  I navigate to the target web page, click on the three-button menu launcher at the upper right of Chromium, choose "More Tools," and then "Add to Desktop."  I then have an icon on my desktop that launches the desired web page in its own window.

I have been doing this for years, on several machines.  Within the past few months, a problem developed on just one of my machines.  The problem is this: When I launch one of these "desktop apps," a full instance of Chromium ALSO opens.  I have to then close this additional instance.  I don't know what caused this change in behavior.  I have the same version of Chromium (Version 59.0.3071.109 (Developer Build) Built on Ubuntu , running on LinuxMint 17.1 (32-bit)) running on several machines; but the problem only occurs on one of them.

Any thoughts on why this unwanted behavior arose, and/or how to kill it?

Many thanks![/FONT][/SIZE]

---

### Post by Iggy64 on 2017-08-08
After much further researching, I found the solution to my problem:  On the computer in question, I had installed the Google Keep extension to Chromium.  It turns out that Google Keep wants you to sign in to Google at startup, so that it can sync your Keep info with your other devices.  Therefore, Chromium will always open with an extra tab (in the foreground), asking you to sign in.  (I wondered why that was happening.)

Therefore, when you launch a Chromium web app from a desktop launcher, Chromium does launch the web app; but it also wants to ask for a sign in.  Because it cannot insert a new tab in the web app window, it launches a new instance of Chromium, complete with the sign-in tab.

Solution: Disable the Google Keep extension.  Now all is well.

---

### Post by monkeybrain20122 on 2017-08-08
> **Iggy64 said:**
> [SIZE=2][FONT=arial]I regularly create desktop shortcuts to web apps using the Chromium browser.  I navigate to the target web page, click on the three-button menu launcher at the upper right of Chromium, choose "More Tools," and then "Add to Desktop."  I then have an icon on my desktop that launches the desired web page in its own window.

I have been doing this for years, on several machines.  Within the past few months, a problem developed on just one of my machines.  The problem is this: When I launch one of these "desktop apps," a full instance of Chromium ALSO opens.  I have to then close this additional instance.  I don't know what caused this change in behavior.  I have the same version of Chromium (Version 59.0.3071.109 (Developer Build) Built on Ubuntu , running on LinuxMint 17.1 (32-bit)) running on several machines; but the problem only occurs on one of them.

Any thoughts on why this unwanted behavior arose, and/or how to kill it?

Many thanks![/FONT][/SIZE]
When you create the web app check the box "open as window" then the other tabs won't open.

---

### Post by Iggy64 on 2017-08-09
Thanks for your suggestion, monkeybrain.  In my case, though, I already have my web apps "open as window."  When the web app window would open, an _additional_ instance (window) of Chromium would open, displaying all my old tabs, plus a new tab asking me to log in (to Google).

As noted in my response above, I finally realized that the Google log-in tab was the problem.  A while back, I installed the Google Keep extension to Chromium.  Subsequently, whenever I would launch Chromium, I was presented with an extra tab asking me to log in.  Very annoying.  I did not realize at the time that this was caused by the Google Keep extension, which apparently wants you to log in so it can sync your other devices.  

When I would launch a web app in its own window, Chromium had no way to present an additional log-in tab in that restricted window, so it launched a whole new instance, complete with the log-in tab.

My solution was to disable the Google Keep extension.  That eliminated the annoying extra time in Chromium, as well as the extra instance of Chromium when I launch a web-app window.

So, problem solved.  Still, I appreciate your interest and suggestion.

---

