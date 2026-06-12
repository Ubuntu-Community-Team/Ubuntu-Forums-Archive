---
title: "Firefox 55 does not use system font for UI or webpages"
date: 2017-08-15
forum: General Help
---

### Post by Infamous Blob on 2017-08-15
Hi,
Since upgrading to Firefox 55, Firefox no longer uses the system font in the UI or on webpages as it did prior. There were issues in previous versions of Firefox, but I used the "gfx.font_rendering.fontconfig.fontlist.enabled = false" work around in order to force it to do so. This setting in about:config appears to have been depreciated in Firefox 55 based on my reading (something to do with [https://bugzilla.mozilla.org/show_bug.cgi?id=1285533](https://bugzilla.mozilla.org/show_bug.cgi?id=1285533)). Does appear though that Firefox should support bitmap fonts, which I assumed was the problem, but another report claims this was patched ([https://bugzilla.mozilla.org/show_bug.cgi?id=1350783](https://bugzilla.mozilla.org/show_bug.cgi?id=1350783)).

I'm currently using Nimbus Sans L as my system font. The problem exists with other fonts and regardless of how much I play with the Font settings in Appearance Preferences. The same problem also exists in Zotero, which would be expected considering how it is Firefox based. The problem continues with a new profile.

Using Ubuntu Mate 16.04.3. Screenshot attached demonstrating the problem. Also available:
[https://www.dropbox.com/s/vjwaveu4nbsh49w/Screenshot%20at%202017-08-15%2022%3A34%3A25.png?dl=0](https://www.dropbox.com/s/vjwaveu4nbsh49w/Screenshot%20at%202017-08-15%2022%3A34%3A25.png?dl=0)
in higher quality.

All help appreciated.
Thanks :)

---

