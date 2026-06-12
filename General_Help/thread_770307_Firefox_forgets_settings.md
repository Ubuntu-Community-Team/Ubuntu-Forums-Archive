---
title: "Firefox forgets settings"
date: 2008-04-27
forum: General Help
---

### Post by syd2o2 on 2008-04-27
I have 8.04 version installed with Firefox 5 beta 5. This is the problem, I go to preferences and set say the option to show my windows and tabs from last time, and turn on the option to always show tabs. Then I close firefox that has a few tabs open. When I start it again, it opens only one tab (my home page) and it has forgotten all the changes to settings I've made.
If it'll help, I have two plugins installed, adblock and addblock updater.
How do I make firefox remember it's settings?

---

### Post by quixotic-cynic on 2008-04-27
Unless the boxes you ticked in the the Preferences section are unticked when you go back I would suppose that the problem is getting the setup right rather than a problem with forgotten settings.

I interpret the "always show tabs" option as referring to "Always show the tab bar", which is related to whether the tab bar shows when you only have one tab open (it usually hides).

I assume that you have 'when firefox starts "show my windows and tabs from last time"' selected.

Try disabling all addons temporarily (in Tools > Addons), restart the browser, open a few tabs, close it and see if the browser remembers... try Adblock Plus if it turns out that your plugins are the problem.

You could also try typing about:config in the address bar and make sure "browser.sessionstore.enabled" and "browser.history.showSessions" are set to true. You also need to make sure that you are not disabling you browser history / clearing all your user data on exit - which would be at odds with what you want.

As a stopgap measure, Ctrl+H bring up the history side bar - you can right click on a folder and open all the pages in that folder in tabs.

Post related: [http://ubuntuforums.org/showthread.php?t=766456](http://ubuntuforums.org/showthread.php?t=766456)

---

### Post by catalina on 2008-04-27
Hi there,

After my upgrade many of the firefox extensions do not work with ff3.  Check to see if you have the right version of adblock (compatible with ff3 and not ff2).  If you go to the add-on web-site the non-compatible add-ons will be greyed out.

This was a hassle for me because many of the add-ons that I had been using (including themes) are not updated for ff3 yet.

Hope this helps.

---

### Post by syd2o2 on 2008-04-27
It's not the extensions. I turned them off, and it's still the same.
I looked the browser.history.showSessions, and it's set to false. I turn it to true, close and start firefox again, and settings are forgotten again, and browser.history.showSessions is again set to false. So it appears to be something about that.

---

### Post by quixotic-cynic on 2008-04-27
Hmm, ok, it definitely does seem like it's not saving stuff.

Try running *firefox -ProfileManager*, creating a new profile and then trying with that one.

Also, you could try checking the read/write permissions on your prefs.js file in your firefox user profile directory (path e.g.: /home/username/.mozilla/firefox/*.default/prefs.js
 ) to make sure it hasn't been set to root or something.

---

### Post by syd2o2 on 2008-04-27
Yup, that was it. Permissions on the prefs.js were set to root for some reason. Changed it to my user, and it's working correctly now. Thanks.

---

### Post by SaintDanBert on 2010-10-19
> **syd2o2 said:**
> Yup, that was it. Permissions on the prefs.js were set to root for some reason. Changed it to my user, and it's working correctly now. Thanks.

[highlight]What a crock of shot...[/highlight]
A program needs to write a file.
File permissions prevent the write.
The program keeps running (this part is okay) but never complains about a major resource that it cannot access.
OH!? We want to avoid on-screen clutter like error messages? What happened to a log file entry or similar?

"Above all else, do no harm..." Which is more harmful to the linux new experience, errors without messages leaving the end-user to wonder and tinker -- OR -- an error dialog or log entry. The choice is easy for me.

Cheers,
 ~~~ 0;-Dan

---

