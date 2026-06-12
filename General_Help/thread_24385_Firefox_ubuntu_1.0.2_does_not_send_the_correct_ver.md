---
title: "Firefox ubuntu 1.0.2 does not send the correct version in user agent"
date: 2005-04-06
forum: General Help
---

### Post by IdoMcFly on 2005-04-06
When I connect to a web site with Firefox from hoary ubuntu it does not return the correct version in my webserver log : 1.0 instead of 1.0.2
using ```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.6) Gecko/20050405 Firefox/1.0 (Ubuntu package 1.0.2)
```

---

### Post by dewey on 2005-04-06
Because, if you check in the about section, it's user agent is indeed,
```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.6) Gecko/20050405 Firefox/1.0 (Ubuntu package 1.0.2)
```

It's still considered firefox 1.0, it's just revision 2.  The difference being, it contains mainly bug fixes, as opposed to being a full release.

If you really want to change your version number in your user agent, to 1.0.2, then simply go to the url "about:config" and modify the value of "general.useragent.vendorSub"

---

### Post by IdoMcFly on 2005-04-07
so it is not based on firefox 1.0.2 ?

---

### Post by IdoMcFly on 2005-04-09
[QUOTE=IdoMcFly]so it is not based on firefox 1.0.2 ?[/QUOTE]
 Maybe I was not understandable.

I mean, which the version of the Firefox shipped with hoary? 1.0 patched by ubuntu, 1.0.2 recompiled by ubuntu?

how it is compared to the official firefox?

---

### Post by jdong on 2005-04-09
That's what official Firefox sends, too. The .2 is a minor revision that does not affect browser behavior, and is not reported.

---

### Post by IdoMcFly on 2005-04-09
[QUOTE=jdong]That's what official Firefox sends, too. The .2 is a minor revision that does not affect browser behavior, and is not reported.[/QUOTE]
 I'm talking about this because I do experience diffrence : I have a website using dotclear and have bbclone installed. It record somehow the user agent and version. At work (Windows-firefox 1.0.2) I got 1.0.2 in my logs. with ubuntu I got 1.0
That's why I'm asking :)

---

### Post by jdong on 2005-04-09
Does it *really* affect browsing in any way? Not really. The prudent webmaster would use the Gecko version string anyway.

---

### Post by IdoMcFly on 2005-04-09
[QUOTE=jdong]Does it *really* affect browsing in any way? Not really. The prudent webmaster would use the Gecko version string anyway.[/QUOTE]
 It does not affect le browsing but my log :) but my question was how is the ubuntu firefox compared to the official one ? can it be considered as a 1.0.2 ?

---

### Post by jdong on 2005-04-09
Yes, it can be considered 1.0.2. It has all the 1.0.2 fixes, plus some Ubuntu/Debian specific patches.

---

