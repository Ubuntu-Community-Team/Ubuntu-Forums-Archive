---
title: "Inconsistency in Firefox from repository"
date: 2007-06-17
forum: General Help
---

### Post by ym4546 on 2007-06-17
I am experiencing an interesting phenomenon that I can't seem to figure out.

I'm on Kubuntu Feisty, and I like to use the KDE App called Akregator as my RSS reader. However, I also like to use Firefox as my web browser. As of version 2.0, Firefox introduced the ability for Firefox users to select an external application as the default RSS application.

Now because Akregator requires an application to use the  "-a" switch when sending a URL to be added as a feed, I had to use a short script I found as the selected application in firefox. The script I found came from [http://porpoisehead.net/hi/?q=node/25](http://porpoisehead.net/hi/?q=node/25) (the top script, not the one with podcast support and all).

Now, initially when I tried this, I was using Firefox 2.0.0.4 from the Ubuntu repository. Even though this is the latest version, Firefox simply refused to use my script. When I clicked on an RSS feed, it would not launch Akregator as set in my settings. However, I then also downloaded Firefox as a tarball directly from Mozilla's website. This was also version 2.0.0.4. Interestingly enough, this version of Firefox behaved correctly when I clicked on an RSS feed.

I was wondering if anyone else has experienced a similar problem. If they could confirm it, perhaps it should be reported as a bug. (I'm not sure how the two versions can exhibit different behavior... they're compiled from the same source code aren't they?)

In any case, the workaround is to simply not use the version from the repository, but I think that it would be great if we could solve this problem in the repository version to keep Ubuntu as hassle-free as possible.

---

### Post by longlegs on 2007-06-21
Did you use md5checksum to verify the downloads?
A faulty download could make the two appera different.
Good luck
longlegs

---

