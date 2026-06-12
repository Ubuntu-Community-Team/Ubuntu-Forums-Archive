---
title: "Why is enabling browser cache insecure?"
date: 2007-03-21
forum: General Help
---

### Post by newbie22 on 2007-03-21
Why is enabling cache considered insecure in browsers?

Something I read about JavaScript, cookies, and cache.  The JavaScript and cookies I understand because of the possible exploits.  But why the cache?

---

### Post by Tomosaur on 2007-03-21
It is theoretically possible for a website to use javascript and other web techonlogies to read what's in your cache and thus deduce where you've been, amongst other things. Depending on the websites you visit, you may also be storing personal information which you would otherwise delete. It really depends on how well made your browser is. The cache will store pretty much anything possible to make your web experience a bit faster, but, depending on how securely the websites you visit are designed, your cache may contain private information which you submit to sites.

Most modern browsers have an 'empty cache' shortcut, or a 'delete private data' shortcut. Use them well :)

You can also set most modern browsers to automatically clear the cache when you close the browser.

---

### Post by dcstar on 2007-03-21
> **Tomosaur said:**
> It is theoretically possible for a website to use javascript and other web techonlogies to read what's in your cache and thus deduce where you've been, amongst other things. Depending on the websites you visit, you may also be storing personal information which you would otherwise delete. It really depends on how well made your browser is. The cache will store pretty much anything possible to make your web experience a bit faster, but, depending on how securely the websites you visit are designed, your cache may contain private information which you submit to sites.
......

And - in theory - a Scumware writer could split up some code so that an innocent-looking part may be able to bypass detection and be stored in a Browser Cache, which subsequently could be extracted and joined up with other innocent-looking portions to create a nasty piece of software which has bypassed all previous detection methods........

---

### Post by jrusso2 on 2007-03-22
Best thing is the no-script plugin for firefox. You can whitelist the safe sites and no script on the rest makes it pretty safe.

Jeanette

---

### Post by newbie22 on 2007-03-23
So you are saying no-script plugin + enabled cache is okay?

---

