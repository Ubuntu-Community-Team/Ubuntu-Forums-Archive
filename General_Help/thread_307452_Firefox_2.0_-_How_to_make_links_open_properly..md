---
title: "Firefox 2.0 - How to make links open properly."
date: 2006-11-26
forum: General Help
---

### Post by Cronjob on 2006-11-26
So, now that I've installed 6.10, I moved to Firefox 2.0 and would sure love to find a way to make clicking on links behave sanely instead of every single link opening in another tab or window. What happened to just opening a link in the same tab you clicked on it in, unless you were holding CTRL?

I can't find anything in the interface and no complaints or solutions via google. I can't be the only one wondering. Thanks.

---

### Post by vtel57 on 2006-11-26
> **Cronjob said:**
> So, now that I've installed 6.10, I moved to Firefox 2.0 and would sure love to find a way to make clicking on links behave sanely instead of every single link opening in another tab or window. What happened to just opening a link in the same tab you clicked on it in, unless you were holding CTRL?

I can't find anything in the interface and no complaints or solutions via google. I can't be the only one wondering. Thanks.

Get the extensions --> Tab Browser Preferences and Tab Clicking Options. I've been using them since the old Mozilla days. 

Luck!

---

### Post by Cronjob on 2006-11-26
That's really bizarre. They build-in the functionality for session-saving (but only on a crash/restart) but then they take out the ability to really control link behavior. Two steps forward; one step back.

Thanks for the tip.

---

### Post by PrinceArithon on 2006-11-26
Well there is a really really REALLY simple solution.

In the browser go to Edit > Preferences.  Then from there click on Tabbed Browsing.  From there you can customize how you want the tabs to work.

---

### Post by noynac on 2006-11-26
You may need to change the following about:config preferences. I have set both to 1 to avoid the behavior you describe. 

browser. link. open_external
browser. link. open_newwindow

You can read more about these preferences at:

[http://tinyurl.com/8swbh](http://tinyurl.com/8swbh)

If the above doesn't help, you should check your user.js file to insure that no conflicting user preferences are contained in that file.

---

### Post by brottman on 2006-11-26
The biggest problem I have is to get Firefox always open links in a tab, but NEVER a new window. It drives me insane every time I click a link and FF opens a brand new window. Just open a new freaking tab!

BTW I have looked through preferences in FF 20 times there is no preference to force links into a tab.

---

### Post by brottman on 2006-11-26
Saw your post right after I sent mine Noynac. Thanks for the info, that was what I was looking for :)

---

### Post by Cronjob on 2006-11-28
> **PrinceArithon said:**
> Well there is a really really REALLY simple solution.

In the browser go to Edit > Preferences.  Then from there click on Tabbed Browsing.  From there you can customize how you want the tabs to work.

Yes, you can choose for new pages to be opened in "a new tab" or "a new window". Neither of those are the options I want and by default, Firefox 2.0 opens in new tabs, which most people do not want. The other three options (include always opening in the same tab) that were there in 1.5 no longer exist.

Manually editing about:config resolved the problem, but this is sure going to turn off a lot of people who are tired of everything popping open a new tab or window and - finding that there is no longer any preferable option in the preferences for them - will just give up on Firefox. Seems the people we're trying to woo to Firefox at this point are largely not the kind like you and I who will install extensions or dig around for hidden config values that have to be set manually (not a big deal for us, but maybe a big deal for my little sister, grandmother, the baker across the street I tried to convert)...

Anyway, problem solved. Thankfully! :)

---

### Post by strabes on 2006-11-28
@brottman - use the "Tabbrowser Preferences" extension. It allows you to configure where to open links that are set to target="_blank" (new window tag). I have it set to open in new tabs. Pretty useful. Get it [here](https://addons.mozilla.org/firefox/158/).

---

