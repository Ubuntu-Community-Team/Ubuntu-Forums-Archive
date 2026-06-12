---
title: "Help: firebox 3 stopped asking to save tabs"
date: 2008-03-25
forum: General Help
---

### Post by jonathanmotes on 2008-03-25
Does anyone know how to turn this feature back on? I guess it is possible that I accidentally checked the "do no show me this again" box when closing my browser.

UPDATE: it is working sometimes (just now it did) so I didn't accidentally turn it off. I guess there is a bug somewhere. I'm using beta 3 still, so that might be the problem.

Thanks!

---

### Post by fela on 2008-03-25
i think you might be able to reset all of the dialogs from the preferences dialog (look around)

---

### Post by jonathanmotes on 2008-03-25
> i think you might be able to reset all of the dialogs from the preferences dialog (look around)

I've looked in preferences and didn't see anything. Thanks anyway.

---

### Post by gaussian on 2008-03-25
It seems that this is controlled (at least for Firefox 2) by preference setting "browser.tabs.warnOnClose". There are two ways to switch that back:

1. Type about:config into the address bar. After a warning message you get a screen with all firefox internal setting. Search for browser.tabs.warnOnClose and set it back to true. 

or

2. Go to you firefox profile folder ~/mozilla/firefox/somerandomletters/ and create a file called user.js with following content:
```
user_pref("browser.tabs.warnOnClose", true);

```

Added: You will need to restart Firefox for these changes to have an effect

---

### Post by jonathanmotes on 2008-03-25
>  It seems that this is controlled (at least for Firefox 2) by preference setting "browser.tabs.warnOnClose".

I was wondering if that was the option under about:config. It is set to true so I guess it's a bug. I need to figure out how to install Firefox 3 Beta 4!

Thanks!

---

### Post by gottifour on 2008-03-25
You should try tabmix plus..Its an addon and it adds a lot of nice features..

I know this doesnt answer your original question but it may help you out..

---

### Post by gaussian on 2008-03-25
Played around with Beta 4 a little. This definitely seems to be a bug (I will look around bugzilla to find if there is a bug there). There is a Preference check box in Firefox since version 1.5 under Preferences/Tabs to change this behavior. In Firefox 3 Beta 4 that preference does not seem to work. 

However what seems to work is a new variable: browser.warnOnQuit that you should set to true.

Added: this seems to be a know bug: [https://bugzilla.mozilla.org/show_bug.cgi?id=412640]("https://bugzilla.mozilla.org/show_bug.cgi?id=412640")

---

### Post by jonathanmotes on 2008-03-25
> However what seems to work is a new variable: browser.warnOnQuit that you should set to true.

Thanks! That seems to do the trick (it was set to false)!

---

### Post by jonathanmotes on 2008-03-25
It is still working properly with browser.warnOnQuit set to true after several tests. This only recently started happening. It has been working properly on Beta 2 and 3 for months! (Strange). You are right about the preferences option - it doesn't seem to be working.

Hummm. Should I mark as solved since you found a workaround?

Thanks again gaussian!

---

### Post by gaussian on 2008-03-26
> **jonathanmotes said:**
> It is still working properly with browser.warnOnQuit set to true after several tests. This only recently started happening. It has been working properly on Beta 2 and 3 for months! (Strange). You are right about the preferences option - it doesn't seem to be working.

Hummm. Should I mark as solved since you found a workaround?

Thanks again gaussian!

Glad to help. I would not mark it as solved, since the GUI thing clearly does not work. You could add the info about browser.warnOnQuit

---

