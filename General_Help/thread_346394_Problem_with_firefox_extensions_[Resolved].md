---
title: "Problem with firefox extensions [Resolved]"
date: 2007-01-25
forum: General Help
---

### Post by Kimm on 2007-01-25
I'm having some trubble with a couple of extentions in firefox (GSpace and DownloadWith).
Whenever I try to use eighter of them, I get an error message that looks like this (they are almost exactly the same)

> 
DownloadWith: Connot run executable: [Exception... "Component returned failure code: 0x80520001 (NS_ERROR_FILE_UNRECOGNIZED_PATH)
[nslLocalFile.initWithPath]" nsresult: "0x80520001
(NS_ERROR_FILE_UNRECOGNIZED_PATH)" location: "JS frame :: chrome://downloadwith/content/objDwUtils.js :: anonymous :: line 42" data: no]


I've tried reinstalling the extentions, I've tried reinstalling firefox both from the repos and from getfirefox.com, but nothing makes any difference (I even tried downgrading to Firefox 1.5)

:confused:

---

### Post by aysiu on 2007-01-25
Maybe file a bug report with the extension maintainers?

---

### Post by Kimm on 2007-01-26
> **aysiu said:**
> Maybe file a bug report with the extension maintainers?

I doubt its a problem with the extensions (since GSpace used to work). But rather a firefox problem, perhaps caused by some other application.

---

### Post by aysiu on 2007-01-26
There's only way to be sure.

Paste this command into the terminal: ```
mv ~/.mozilla ~/.mozilla.original
``` Launch Firefox and see if you run into the same problem.

If you don't, then the extensions were the problem, and you should probably do something like [this](http://ubuntuforums.org/showthread.php?t=103930) to get a fresh profile and keep your bookmarks.

If you do, then you're right--it's a problem with Firefox.

---

### Post by Kimm on 2007-01-26
Thanks!
That fixed it!

---

### Post by aysiu on 2007-01-26
> **Kimm said:**
> Thanks!
That fixed it!
Great!

---

