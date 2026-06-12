---
title: "No Flash Video on Firefox 28 &amp; Chrome; Works on Chromium; FF Crashing"
date: 2014-04-18
forum: General Help
---

### Post by buzzingrobot on 2014-04-18
Firefox 28 here on 14.04 is not playing Flash video, displaying black instead. It's the Flash installed in the restricted package.  

In addition, occasionally a Flash request dialogue will popup over the black rectangle asking for permission to store data locally.  The dialogue does not respond to the mouse and cannot be dismissed.

FF28 is also crashing frequently on launch.  

Disabling all extensions didn't affect the Flash problem or the crashing.

I first saw both behaviors begin during the last few days before 14.04's release, and it's continued past the release.

Oddly, while it isn't crashing, Flash isn't working on Chrome either.  But, it is working on Chromium.  Odd because they both use PepperFlash.

Finally, is there supposed to be an environmental variable pointing to the Flash plugin?  Something like $Moz_Plugin_Flash_Path?  There isn't here.

[LATER:  The culprit seems to be the EFF's 'HTTPS Everywhere' addon. I purged Firefox and Flash, removed ~/.mozilla, then installed Firefox and Flash.  Flash worked fine with no extensions.  I added my usual extensions one at time, and Flash worked after each install.  Added HTTPS Everywhere and Flash videos stopped working.  Removed HTTPS Everywhere and Flash videos worked again. However, I still see occasional Flash Settings request dialogues that ask for permission to store data locally but do not respond to the mouse and cannot be dismissed.  The video plays behind them.]

---

### Post by joaov-ferreira on 2014-04-25
Had the same problem here and I'm using this same extension, gonna try this

[UPDATE] Removed this extension and now flash works

---

