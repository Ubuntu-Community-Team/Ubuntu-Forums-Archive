---
title: "Bank of America's SafePass does not like flash player"
date: 2008-02-15
forum: General Help
---

### Post by geek_sandy on 2008-02-15
Hi!

Recently BofA introduced this security feature called SafePass, which sends an SMS message with a pass code to a cell phone to perform some critical things. One of such critical things is logging in for the first time from a new computer. The problem is that it relies on a flash player, and it does not like the one in Ubuntu 7.10 with all the latest updates:

"This feature requires you to have JavaScript enabled and have an updated Flash player. To perform this SafePass-protected action, you must turn on JavaScript in your browser settings and/or update your Flash player to the latest version. Then you’ll need to close this browser, open a new window, and sign in again."

YouTube plays just fine.
Any Ideas?
Thanks.

---

### Post by Het Irv on 2008-02-15
Do you have Java Script fully enabled (Edit->Prefrences->Content)?  Do you have the NoScript add-on for Firefox, if so make sure that it is enabled for BofA.

---

### Post by geek_sandy on 2008-02-15
>Do you have Java Script fully enabled (Edit->Prefrences->Content)?

Yes

> Do you have the NoScript add-on for Firefox, if so make sure that it is enabled for BofA.

How do I check this? I did not explicitly install such thing or restricted any sites, so I am not aware of this.

What makes you think that it is a JavaScript problem? I assumed that JavaScript was fine, since it is quite a basic thing, and everything looks fine on all web sites I visit. So I thought it must be Flash.

Do you use the SafePass feature?

---

### Post by Het Irv on 2008-02-15
No, I don't use it.  JavaScript was just one idea I had that was easy to check.  Also, if you don't remeber installing NoScript, you most likly don't have it.  Have you tried getting the flash player directly from the Adobe site.  If the newest one doesn't work try older versions just in case (yes, I know it is asking for a more up-to-date version).

---

### Post by geek_sandy on 2008-02-15
> **Het Irv said:**
> No, I don't use it.  JavaScript was just one idea I had that was easy to check.  Also, if you don't remeber installing NoScript, you most likly don't have it.  Have you tried getting the flash player directly from the Adobe site.  If the newest one doesn't work try older versions just in case (yes, I know it is asking for a more up-to-date version).

As far as I understand from [http://noscript.net/](http://noscript.net/), NoScript is for extra protection, so it should not help me to make it work. It should help me to block such things on a per-site basis. It is a good idea, but I don't see how it can help in this particular case.

With respect to Flash, I am not quite sure if Flash or Gnash are used and at fault. How do I know which player is used in this case?

I think anyone can give it a test drive without being a BofA customer here:
[http://www.bankofamerica.com/privacy/index.cfm?template=learn_about_safepass](http://www.bankofamerica.com/privacy/index.cfm?template=learn_about_safepass)
or here
[http://www.bankofamerica.com/onlinebanking/safepass/flash/index.cfm](http://www.bankofamerica.com/onlinebanking/safepass/flash/index.cfm)

---

### Post by FuturePilot on 2008-02-15
Type
```
about:plugins
``` in the browser address bar.
Also if 
```
apt-cache policy mozilla-plugin-gnash
``` says you have gnash installed, remove it, it doesn't play nicely alongside Adobe's Flash
```
sudo apt-get remove --purge mozilla-plugin-gnash
```

---

### Post by geek_sandy on 2008-02-16
> **FuturePilot said:**
> Type
```
about:plugins
``` in the browser address bar.
Also if 
```
apt-cache policy mozilla-plugin-gnash
``` says you have gnash installed, remove it, it doesn't play nicely alongside Adobe's Flash
```
sudo apt-get remove --purge mozilla-plugin-gnash
```

Cool, this worked just fine. And it seems to be a little faster than Gnash.
Thanks a lot.

---

