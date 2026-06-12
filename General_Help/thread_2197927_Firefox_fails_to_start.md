---
title: "Firefox fails to start"
date: 2014-01-06
forum: General Help
---

### Post by bugbear6502 on 2014-01-06
I let update manager do a big (249Mb) update this morning on 13.10, and when starting
firefox I now get a window popping up containing:
```

XML Parsing Error: undefined entity
Location: chrome://browser/content/browser.xul
Line Number 1083, Column 9:

<button id="identity-popup-help-icon"
--------^
```

And nothing else.

It appears that this "file" (browser.xul) is effectively Firefox's
user interface (!!), so my guess is that a LOT of bugs could have this
error signature.

Has anyone else seen this, or do I (somehow) have a unique fault
on my machine?

 BugBear (posting from work laptop/seamonkey)

---

### Post by bugbear6502 on 2014-01-06
Reverting from version 27.0~b2+release-0ubuntu1+yasi1 down to 26.0+build2-0ubuntu0.13.10.2 fixed the problem, so I'll wait for a fix on 27.0, which appears to be fatally bugged.

In case anybody else read this, the command to fix was:

sudo apt-get install firefox=26.0+build2-0ubuntu0.13.10.2

Does anyone know how to stop a "general" apt-get upgrade from giving me v27 again?

 BugBear

---

### Post by bugbear6502 on 2014-01-07
> **bugbear6502 said:**
>  

Does anyone know how to stop a "general" apt-get upgrade from giving me v27 again?

 BugBear

(from 
[http://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package](http://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package)
)

**Using apt**
  *you can hold a package using*
  sudo apt-mark hold package_name
  *and remove the hold with*
  sudo apt-mark unhold package_name

Thanks to all who helped.

 BugBear

---

### Post by bugbear6502 on 2014-02-25
Firefox is now working OK for me, after I risked a recent update.

 BugBear

---

