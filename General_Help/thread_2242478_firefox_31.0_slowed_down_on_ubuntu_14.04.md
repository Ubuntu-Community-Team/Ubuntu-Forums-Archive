---
title: "firefox 31.0 slowed down on ubuntu 14.04"
date: 2014-09-02
forum: General Help
---

### Post by Hodor on 2014-09-02
Hi, 
my firefox 31.0 has slowed down significantly over a period of some weeks / months - on ubuntu 14.04.  
Never exactly zippy, but better than this before.
sometimes just refuses to load a page - gives wierd messages (no javaScript support).
Any advice?

Thanks

---

### Post by Cliff_Simonds on 2014-09-02
Firefox 32 is out now anyhow, just not in the repositories yet. But have  you tried clearing all of firefoxes history, updating add-ons, and  clear dns cache using ```
sudo /etc/init.d/dns-clean restart
```?

---

### Post by claracc on 2014-09-02
You can try to disable all the addons you have in firefox and then enable one by one to see if any of them is slowing the browser.

---

### Post by Hodor on 2014-09-02
Thanks Cliff_Symonds - how do I update add-ons

---

### Post by Cliff_Simonds on 2014-09-02
In Firefox>tools>add-ons>gear icon at the top with dropdown menu>check for updates

---

### Post by vasa1 on 2014-09-02
> **Cliff_Simonds said:**
> Firefox 32 is out now anyhow, just not in the repositories yet. ...
Just got an 18 MB update to v32; my Firefox is direct from Mozilla and not the one from the repos. At first glance, there are no obvious differences and no breakage in the UI.

FWIW, the release notes are here: [https://www.mozilla.org/en-US/firefox/32.0/releasenotes/](https://www.mozilla.org/en-US/firefox/32.0/releasenotes/)

---

### Post by Hodor on 2014-09-08
Thanks claracc, disabled a few of these and its like my browser has come off the dope.

---

### Post by Hodor on 2014-09-08
Thanks Cliff_Simonds

---

### Post by Cliff_Simonds on 2014-09-09
> **Hodor said:**
> Thanks Cliff_Simonds

Glad I could help. God only knows how these forums have helped me too.

---

### Post by claracc on 2014-09-09
> **Hodor said:**
> Thanks claracc, disabled a few of these and its like my browser has come off the dope.

You are very welcome.

If you have fixed your problem, please mark the thread as solved with thread tools menu in the right upper part of the page.

Thanks.

Also, what is the culprit addon ?

---

### Post by Hodor on 2014-09-10
Turning off firefox health reporter also seems to speed things up - this is a little annoying because I've turned it off previously, but it seems to reset to a default 'on' after upgrades or some such, so you need to remember to periodically check.

---

### Post by Hodor on 2014-09-10
Hi claracc,
not really sure - I ended up disabling all of them (and this seems to cause problems with the browser connecting with the server on occaisions).  I think I jumped to the conclusion the browser had sped up too soon - after I posted this message above, it slowed down again.  Adding adblock plus seems to have improved things.  Turning off health reporting also improved things (I noticed while the browser was slowing loading a page, some of the messages at the bottom were related to old pages, not the current).  But the browser is still significantly slower for e.g. a google search than google chrome - so I think I'll go with that.  I'll mark the problem as solved since it has sped up somewhat at present, but I think I'm dissapointed with Firefox's performance.

---

### Post by nick3499 on 2015-08-30
after
`sudo apt-get purge xul-ext-webaccounts`
my Firefox sped up

---

