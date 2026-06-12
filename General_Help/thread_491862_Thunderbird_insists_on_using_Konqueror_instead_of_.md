---
title: "Thunderbird insists on using Konqueror instead of Firefox"
date: 2007-07-04
forum: General Help
---

### Post by jespdj on 2007-07-04
I am using Kubuntu 7.04 (64-bit).

I have installed Mozilla Firefox and Thunderbird, and in the KDE system settings I set Firefox as my default web browser (instead of Konqueror). This works, when I click on a web link in most KDE programs Firefox is now opened instead of Konqueror.

However, when I click on a link in an e-mail in Thunderbird, it still opens Konqueror instead of Firefox. How can I make Thunderbird use Firefox? I can't find any setting in the Thunderbird preferences to set the browser...

---

### Post by Brucevdk on 2007-07-04
You could try selecting */usr/bin/firefox* from:
```

sudo update-alternatives --config x-www-browser

```

---

