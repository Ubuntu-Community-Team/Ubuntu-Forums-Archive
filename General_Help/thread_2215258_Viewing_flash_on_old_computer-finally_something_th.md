---
title: "Viewing flash on old computer-finally something that works."
date: 2014-04-05
forum: General Help
---

### Post by Larry_Klein on 2014-04-05
I am only a couple weeks into my transformation from Win XP to linux.

First - lubuntu is the only distro that installs and works well for me.

Most of the last couple weeks was trying to get flash to work for the streaming radio station I enjoy, and live streaming news feeds.

I have tried dozens of things I found on the net, and all browsers,with no luck (or pathetic results). Turns out I have an old ( Athlon XP 2800) processor that lacks SSE2 - whatever that is. And I did go the wine route and it worked- but not really well. Plus it is the same old ugly win app.

SOLUTION!!! I downloaded Opera -new version won't work either - click other versions and choose 11.64, which worked for me. 

Being older, I don't know how secure it is, but I can use it for what I need. Otherwise, it's Firefox.

I would like an older version of Chrome or Chromium that works as well. I haven't had much luck with that.

---

### Post by Larry_Klein on 2014-04-06
I also found the flashplayer that came with Opera ( /usr/lib/adobe/plugins ) , can work in Chromium and Firefox. Just delete the newer ones and copy and paste this one.

delete from

/usr/lib/mozilla

/usr/lib/chromium

paste new one

---

