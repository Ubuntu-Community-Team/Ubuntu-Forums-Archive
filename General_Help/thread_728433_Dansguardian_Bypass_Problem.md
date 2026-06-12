---
title: "Dansguardian Bypass Problem"
date: 2008-03-18
forum: General Help
---

### Post by Jarr0d on 2008-03-18
Hey Guys,

I am having trouble with a installation of DansGuardian on Ubuntu 7.10.

I have configured the lists I need with the sites I need blocked, but there is an extremely easy way to get around the blocked page.

I have blocked [www.bebo.com](www.bebo.com), but if I put this URL in [www.bebo.com/?](www.bebo.com/?) it takes me straight to the website.

Is there a way I can get DG to block this Bypass?

---

### Post by Ushi on 2008-06-03
I know this is an old post, but I found it on Google, and thought I'd chime in.

The problem you are having is that you are blocking the *URL* [www.beebo.com](www.beebo.com) instead of the *site* beebo.com

Put your block into the bannedsites file instead of the bannedurls file, and you will find beebo.com to be inaccessable.

---

