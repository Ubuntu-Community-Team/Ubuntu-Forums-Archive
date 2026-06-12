---
title: "Chrome works but Chromium does not (flash plugin &amp; videos)"
date: 2014-10-18
forum: General Help
---

### Post by michael-piziak on 2014-10-18
Firefox and Google Chrome work fine with all videos; however, Google Chromium often begs for the flash player plug in to be installed - even though that plug in has been installed.

?

I'm using Ubuntu 12.04 lts

---

### Post by Frogs Hair on 2014-10-18
Chrome and Chromium use pepper flash. Chrome includes the flash version when downloaded and for Chromium the  pepperflashplugin-nonfree package needs to be installed.

---

### Post by michael-piziak on 2014-10-18
What's the best way to install the pepper flash so that it only affects my Chromium Web Browser.  I don't want to screw up Chrome or Firefox by adding pepper flash to them when they are already working.

I'm using Ubuntu 12.04 lts

---

### Post by Frogs Hair on 2014-10-18
Look for the package I wrote about in the software-center .

---

### Post by deadflowr on 2014-10-18
You would have to add a ppa for pepperflashplugin-nonfree for 12.04.

But having stated that, I think you can look at the plugins used by chromium the same way as with chrome.
Open a new tab and type in chrome://plugins
I think if you have chrome already installed, then chromium should already be seeing the pepperflash plugin and be using it.
It might be the plugin is disabled.?

---

### Post by vasa1 on 2014-10-19
> **deadflowr said:**
> ...
I think if you have chrome already installed, then chromium should already be seeing the pepperflash plugin and be using it.
It might be the plugin is disabled.?

I don't know whether it's relevant but is it possible that Chromium doesn't pick up the Chrome plugin if there's a version number difference? Right now, Chrome is v38 whereas Chromium is v37.

---

### Post by Frogs Hair on 2014-10-19
> You would have to add a ppa for pepperflashplugin-nonfree for 12.04. deadflowr is correct , I'd forgotten Pepper was not in the repository in 12.04. ;)

---

