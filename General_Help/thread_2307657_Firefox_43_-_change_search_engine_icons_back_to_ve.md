---
title: "Firefox 43 - change search engine icons back to vertical"
date: 2015-12-27
forum: General Help
---

### Post by pickarooney on 2015-12-27
After FF updated to version 43 the layout of the multi-search button has changed to an awkward format. This has been there for a while but I previously had some method of reverting it to the format I prefer.

Attached is how it looks now, with the buttons for the search engines along the bottom. This requires entering the search term and then clicking on the corresponding engine's icon to search. Afterwards there is no visual indication which search engine is currently selected.

Previously, the engines were listed vertically down the side under where you see the magnifying glass now. You could select the engine and then enter a search term. After searching, the icon of the current engine stayed displayed.

I've checked that **ShowOneOffButtons** is set to false in **about:config** and it is

I may have had an extension installed which 'fixed' the search behaviour but I no longer see it installed if that's the case.

---

### Post by vasa1 on 2015-12-27
> **pickarooney said:**
> ... I may have had an extension installed which 'fixed' the search behaviour but I no longer see it installed if that's the case.
"Unsigned" extensions won't work in Fx 43.

In about:config ...
Search for **xpinstall.signatures.required**.
Double-click the preference to set it to **false**.

See if your problem goes away. This fix may not be available when Fx 44 rolls out.

---

### Post by pqwoerituytrueiwoq on 2015-12-27
set this to false in about:config to revert the search feature
browser.search.showOneOffButtons
*this may no longer work :(
edit [http://www.ghacks.net/2015/12/16/how-to-restore-classic-search-in-firefox-43/](http://www.ghacks.net/2015/12/16/how-to-restore-classic-search-in-firefox-43/)

---

### Post by pickarooney on 2015-12-27
That didn't do anything unfortunately

Why must they break things that work right?

---

### Post by pqwoerituytrueiwoq on 2015-12-27
both the link i posted and what vasa1 said work, im using them bow

---

### Post by pickarooney on 2015-12-29
Sorry, I didn't read the ghacks articke fully and hadn't ticked the right box. That solutions works, thanks!

---

