---
title: "Firefox does not warn about closing tabs"
date: 2008-06-27
forum: General Help
---

### Post by riseringseeker on 2008-06-27
Recently the behavior of Firefox has changed.  It used to ask me if I wanted to close all the tabs if I had multiple tabs open and I hit the "X".  Now it just closes all the tabs without any warning, or option to not close them all. 

I have checked the box "Warn me when closing multiple tabs", but they close without warning.  Tried unchecking the box, same thing, closed firefox, opened it again, checked the box again, closed Firefox to try and get it to save the option...  No matter, it still closes the tabs.

What am I missing?

---

### Post by y-lee on 2008-06-27
Type [noparse]about:config[/noparse] into the address bar. In the about config window search for **browser.tabs.warnOnClose**, is it set to false? If so set it to true by double clicking it

If this doesn't work do you have and tab add ons? Try creating a new profile ands ee if you have the same behavior.

```
firefox -P
```

---

### Post by riseringseeker on 2008-06-30
> **y-lee said:**
> Type [noparse]about:config[/noparse] into the address bar. In the about config window search for **browser.tabs.warnOnClose**, is it set to false? If so set it to true by double clicking it

If this doesn't work do you have and tab add ons? Try creating a new profile ands ee if you have the same behavior.

```
firefox -P
```

Nope is set to true in "about:config".  Not sure what you mean about whether I have "tab add ons".  It works the same way on another account, which of course has a different profile.

---

### Post by y-lee on 2008-06-30
> **riseringseeker said:**
> Nope is set to true in "about:config".  Not sure what you mean about whether I have "tab add ons".  It works the same way on another account, which of course has a different profile.

Hmm very odd.

By tab add ons I meant firefox extensions that change the way firefox handles tabs or adds new features to firefoz tabs. [Tab Mix Plus]("https://addons.mozilla.org/en-US/firefox/addon/1122") being a common example of a tab add on.

Did you try creating a new profile

```
firefox -P
```

Regardless of your FF profile on your other user account trying a clean profile would rule out some add on conflict.

Also what version of firefox and what version of ubuntu?

---

### Post by y-lee on 2008-06-30
If you are using firefox 3 it seems the problem you are describing is a "new feature" (or bug depending upon your point of view ;) ) they have added.

> The workaround to set Firefox to warn or ask for confirmation before closing window with multiple open tabs, or quit Firefox application, is to disable session restore by setting Firefox to start up with home page or blank page. To do so, click on **Tools** menu and then **Options**. In the Main tab Startup section, select **Show my home page** or **Show a blank page **for “When Firefox starts” option (Note that “Show my windows and tabs from last time” means session restore, which mean you won’t get any close tabs confirm warning).

After configuring Firefox to load homepage or blank page on startup, Firefox will prompt a “Quit Firefox” titled dialog box, saying “Do you want Firefox to save your tabs for the next time it starts?”. User can select “Save and Quit” to override “When Firefox starts” setting in order to save and restore and reopen all opened tabs that are been closed on next Firefox session, “Quit” to start afresh on home page or blank page (depending on setting above), or “Cancel” to cancel the exit operating and stay in current window.

see [Firefox 3 Doesn’t Prompt or Warn to Confirm When Closing Multiple Tabs As Warning Not Working]("http://www.mydigitallife.info/2008/06/19/firefox-3-doesnt-prompt-or-warn-to-confirm-when-closing-multiple-tabs-as-warning-not-working/")

It seems maybe i should have googled this problem first as it is posted all over the place. :o

---

### Post by riseringseeker on 2008-07-02
> **y-lee said:**
> Hmm very odd.

By tab add ons I meant firefox extensions that change the way firefox handles tabs or adds new features to firefoz tabs. [Tab Mix Plus]("https://addons.mozilla.org/en-US/firefox/addon/1122") being a common example of a tab add on.

None that I am aware of anyway.  Only have a few addons installed.  Forecastbar enhanced, Ubuntu Firefox Modifications, and Web Developer.

> Did you try creating a new profile

```
firefox -P
```


Just did and it does the same thing.  I also see that it does ask about closing tabs, but **only** when I have a second copy of Firefox open, when I close the first copy, Firefox then closes without asking about the tabs that are open.

> Regardless of your FF profile on your other user account trying a clean profile would rule out some add on conflict.

Then that is eliminated, as it does the same with the "test" profile a it does the "Default User" one (and yes, closed Firefox between trying to get it to have any new settings).

> Also what version of firefox and what version of ubuntu?

Firefox reports itself as Version 3.0, it's the one that installed with 8.04 and whatever updates it's had.

Ubuntu reports:
Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7))

---

### Post by riseringseeker on 2008-07-02
> **y-lee said:**
> If you are using firefox 3 it seems the problem you are describing is a "new feature" (or bug depending upon your point of view ;) ) they have added.



It seems maybe i should have googled this problem first as it is posted all over the place. :o

Apparently I didn't search correctly at least.  Things mostly work as described in the article, which of course was not written for Linux users.  Guess I'll just have to live with it, or learn to open a "background" copy before I open tabs.

Thanks for the help.

---

### Post by BLTicklemonster on 2008-07-02
Firefox was asking me if I wanted to save tabs, or just quit, now it just asks if I want to close tabs. (or cancel, in both cases, of course)

It definitely has changed in the past few days. For no reason, but probably since one of the updates.

I click help and about and I am running firefox 3.0.

Strangeness for sure.

---

### Post by loobyloo on 2008-12-17
Hi, I've been getting frustrated with this but I found that someone has found the solution:
[http://warnmewhenclosingmultipletabs.blogspot.com/](http://warnmewhenclosingmultipletabs.blogspot.com/)

Works here on Ubuntu 8.10 / FF 3.0.4

Cliff

---

