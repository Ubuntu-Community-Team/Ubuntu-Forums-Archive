---
title: "&quot;unsubscribe&quot; to emails kinda not working"
date: 2019-09-04
forum: General Help
---

### Post by Autodave on 2019-09-04
Every so often, I really get tired of all the email. So, occasionally, instead of just deleting them I actually scroll to the bottom and click on the *unsubscribe *link.  That takes you to a website where you enter your email address and hopefully you don't get any more junk from them.  However, an interesting thing started about a week ago: when I click the *unsubscribe* link in the email, Firefox opens to the page. But, nothing at all appears on the page.  The site's address is correct, but I am presented with a blank page.  F5 refreshes, but I still have a blank page.

If I close Firefox and then click on the *unsuscribe *link again, I am taken back to the same site, but this time I have a place to type my email into.

Anyone else having this issue?

---

### Post by TheFu on 2019-09-04
Every email list-server (that's what email lists are called) has slightly different processing. Reputable advertising companies will make it easy and not make you enter any email address.  Most will have some javascript to make it harder for 3rd parties to automatically unsubscribe using a simple curl script.

In Firefox, I usually have a few addons. These often make tracking sites unhappy. Just because you want to opt out, doesn't mean they want to make it easy.

I use a different browser, running inside a **firejail** container, that isn't allowed to write anything to disk, for visiting those sort of places - untrusted.
```
$ firejail --private  chromium-browser &
```

---

### Post by Skaperen on 2019-09-04
is that the name of the package to install?  does is work with firefox?  i already compartmentalize by userid.  i'm thinking of adding container layers if i can figure out how to get x to work inside, or have a non-root user start firefox inside.

---

### Post by Holger_Gehrke on 2019-09-04
Do you happen to use the NoScript add-on ? I do and often see pages which will not display anything unless I allow some script to execute.

Holger

---

### Post by Autodave on 2019-09-04
Not using NoScript.  It is really weird that the problem just started a week ago.  It is really weird that it will fail on first try, but work immediately after closing Firefox and then hitting the unsubscribe again.

---

### Post by &amp;KyT$0P# on 2019-09-04
Autodave, are you using uBlock Origin?

When the issue occurs, what if you then just drag&drop the unsubscribe link into Firefox, without restarting Firefox?  Or copy+paste into Firefox address bar?

---

### Post by Autodave on 2019-09-05
I am using uBlock.  I will try your suggestion and see what happens.  Understand that this is not a serious issue, I just thought it was really weird.

---

