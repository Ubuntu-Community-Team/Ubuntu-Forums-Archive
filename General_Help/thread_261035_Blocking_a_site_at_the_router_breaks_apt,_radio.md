---
title: "Blocking a site at the router breaks apt, radio"
date: 2006-09-19
forum: General Help
---

### Post by skymt on 2006-09-19
Okay, so I got sick of seeing those green-underlined text ads from [IntelliTXT](http://intellitxt.com/) (ITXT). They're everywhere, and are worse than pop-ups.

After digging through the source of an IntelliTXT-cursed website, I found that the magic is in a .js file loaded from an ITXT server. It's a different hostname for each website using ITXT. Linux Forums, for example is linuxforums.us.intellitxt.com. I did a few nslookups, and the servers don't seem to be in any particular IP range.

So, since my Netgear router has a handy domain keyword blocker, I simply told it to block everything with "intellitxt.com". That works great. Pages load faster, and there's no sign of green underlining.

However, when the fix is on, "aptitude update" can connect to almost nothing. It just gives me "Connection failed" for most (not all, different each time) entries in my sources.list.

Also, Internet radio gets flaky (stopping randomly). These are just the symptoms I've noticed, there are probably more.

I'd like to do this at the router, so all my computers get the benefit. Any advice?

---

### Post by PriceChild on 2006-09-19
Try adding the adblock extension instead.

[https://addons.mozilla.org/firefox/10/](https://addons.mozilla.org/firefox/10/)

It also contains filter sets which will update.

---

### Post by Ramses de Norre on 2006-09-19
Disabling that domain on my router made sites like linuxforums take minutes to load, firefox waits for the intellitxt server to respond and only if the connection times out it continues to load the parent site..
Aptitude keeps working though.

---

### Post by jISh on 2006-09-19
Also things like NoScript for firefox will do the trick. Never seen one of those ads in my life :D

---

### Post by skymt on 2006-09-19
Things like NoScript and Opera Site Preferences will let IntelliTXT through if you enable JS for a site for other reasons.

I have it blocked at the browser (Opera), with a user script. However, this doesn't solve the delay caused by IntelliTXT. In fact, it increases it, because both the ITXT script and the ITXT blocker script take time to run.

I'd like to block this *at the router*, so all the computers on my LAN get blocking "for free." It's obviously possible, it works, but things break. I'd like to find a way that doesn't break things, if such a way exists.

Thanks for the replies, though!

EDIT: If I can't use the router, I'd like to block it at each computer, but at the network level. Browser-level blocks don't save any time.

---

### Post by skymt on 2006-09-20
One last *bump* before I give up on the router and try a firewall on each computer.

---

