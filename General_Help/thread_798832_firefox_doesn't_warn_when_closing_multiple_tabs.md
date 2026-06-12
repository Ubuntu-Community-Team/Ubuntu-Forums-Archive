---
title: "firefox doesn't warn when closing multiple tabs"
date: 2008-05-18
forum: General Help
---

### Post by i speak in math on 2008-05-18
My firefox doesn't warn me when closing multiple tabs. I have checked and unchecked the box for it in preferences > tabs but either setting results in the same thing...firefox just closes. If I open firefox and, while the tabs are still loading, immediately hit close, then it warns me about closing multiple tabs.

Also, firefox will occasionally stay open in the background. For instance, I closed firefox, did something else on my pc and then tried to open firefox again. It told me firefox is already running and I need to close it before I can open another instance of firefox.

using the supplied firefox 3 beta that came with 8.04.

---

### Post by roe_polak on 2008-05-18
In the Firefox location bar type in "about:config". I will give you a warning that you're entering dangerous grounds and you're fine with it.

At the top you will see a search text area. Type "tabs". You can now fiddle with the way firefox handles tabs. At the bottom there is an option called "Browser.tabs.warnOnClose". Check the value and correct to your needs.

Hope this helps.

---

### Post by i speak in math on 2008-05-18
> **roe_polak said:**
> In the Firefox location bar type in "about:config". I will give you a warning that you're entering dangerous grounds and you're fine with it.

At the top you will see a search text area. Type "tabs". You can now fiddle with the way firefox handles tabs. At the bottom there is an option called "Browser.tabs.warnOnClose". Check the value and correct to your needs.

Hope this helps.

I guess I should have mentioned that I am familiar with about:config. Warn on close is set to true and yet, it does not warn on close.

---

### Post by roe_polak on 2008-05-18
Hmm, strange behavior...

Try to move your ~/.mozilla/ folder from ~/. This will make firefox create a new profile. You will lose bookmarks and personal settings, but I think there are ways to import these. Just try to see if it makes any difference.

---

### Post by i speak in math on 2008-05-18
> **roe_polak said:**
> Hmm, strange behavior...

Try to move your ~/.mozilla/ folder from ~/. This will make firefox create a new profile. You will lose bookmarks and personal settings, but I think there are ways to import these. Just try to see if it makes any difference.

I renames .mozilla to .mozillaOld and it created a new profile. When I closed the window, it presented me with a window asking if I wanted to save my tabs, cancel or quit. This isn't the warning my windows box presents. I can get the correct box to appear by clicking on one of my tabs and choosing close other tabs. 

this is the expected window when closing firefox:
[ATTACH]70596[/ATTACH]

---

### Post by roe_polak on 2008-05-18
I don't quite follow you.

Does Firefox now show the dialog asking if you want to save your session? This is the default behavior of FF3.

---

### Post by i speak in math on 2008-05-18
> **roe_polak said:**
> I don't quite follow you.

Does Firefox now show the dialog asking if you want to save your session? This is the default behavior of FF3.

Ah, I didn't know they changed the default closing warning in v3. I guess this can be closed then

---

### Post by richbl on 2008-06-19
Not sure if this was ever clearly resolved, but I can say that with Firefox 3.0, you will NOT get a warning when closing multiple tabs (or closing the application itself) IF the "Show Windows and Tabs from Last Time" option is active in the Preferences/Main dialog.

This functionality is by design, and suggests the logic that if this option ("Show Windows and Tabs from Last Time") and the user inadvertently closes Firefox, it would just be a matter of reopening the application to get back to where they were initially.

Personally, I feel this is unexpected behavior, as the Firefox developers failed to recognize that a browser restart can sometimes refresh a website, which is NOT the same as picking up from where the user last left off.

As a great example, I regularly listen to pandora.com. If I pause the website (flash-based) player, and then restart Firefox, pandora.com refreshes and begins playing music all over again. You can argue that the design flaw is with pandora.com, but clearly there are any number of websites that refresh on browser restart.

rich

---

