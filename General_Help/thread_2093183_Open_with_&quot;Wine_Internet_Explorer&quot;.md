---
title: "Open with &quot;Wine Internet Explorer&quot;"
date: 2012-12-10
forum: General Help
---

### Post by BuddyThirteen on 2012-12-10
I searched and found a similar thread, but for Xubuntu, back in June or July, but it was unresolved, so I'll ask again and hopefully we can get somewhere.

If I right-click on an image file, after upgrading from 12.04 to 12.10, there is now an option to Open With -> Wine Internet Explorer

That wasn't there in 12.04, and it is neither needed nor wanted. I do not have  WINE installed, and there's no way in Satan's wildest dreams I'd have Internet Explorer installed.

I have installed nearly every game from the Humble Bundles, and I know some of them are run through WINE or ... something. Wine itself is not installed on my system, as software center cannot find it to remove it.

```
dpkg-query: package 'wine' is not installed and no information is available
```As the other thread suggested, I checked  ~/.local/share/applications/ and there are indeed a bunch of wine-extension-*.desktop files in there.

So... what do we do next?
I really don't need that menu option there, and I really don't want that abomination to insinuate that I have IE anywhere on my Ubuntu installation (can't be helped on the Windows side, obviously, but we do what we can).

What do?

---

### Post by vasa1 on 2012-12-10
> **BuddyThirteen said:**
> ... Wine itself is not installed on my system, as software center cannot find it to remove it.
...
Looks like it **was** installed at one time by someone (or pulled in while installing something else?). From what I remember of Wine, it doesn't uninstall cleanly. Additional steps are needed to get rid of traces such as what you are seeing.

---

