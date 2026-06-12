---
title: "Firefox and Click-to-play"
date: 2013-08-11
forum: General Help
---

### Post by vasa1 on 2013-08-11
Firefox is changing the way click-to-play works and that change in seen in Firefox 24 which is now in beta.

There are some links on the subject:
[http://forums.mozillazine.org/viewtopic.php?f=9&t=2723831](http://forums.mozillazine.org/viewtopic.php?f=9&t=2723831)
[http://www.ghacks.net/2013/07/29/firefox-24-restore-click-to-play-per-element/](http://www.ghacks.net/2013/07/29/firefox-24-restore-click-to-play-per-element/)

The old behavior cannot be restored by changing settings in about:config but there's an add-on that does the job:
[https://addons.mozilla.org/en-US/firefox/addon/click-to-play-per-element/](https://addons.mozilla.org/en-US/firefox/addon/click-to-play-per-element/)

I've installed it and it works for Firefox 24.

---

### Post by vasa1 on 2013-08-11
For those who don't want to install an extension, [https://mail.mozilla.org/pipermail/firefox-dev/2013-July/000466.html](https://mail.mozilla.org/pipermail/firefox-dev/2013-July/000466.html) may have some hints:
> 
These prefs already exist as 
plugin.sessionPermissionNow.intervalInMinutes and 
plugin.persistentPermissionAlways.intervalInDays

I haven't tried it but I suspect the number of clicks will be higher than with the extension.

Edit: 
I disabled the extension and used "plugin.sessionPermissionNow.intervalInMinutes;0". 
Now, I can get by without the extension but I need two clicks instead of one: one click on the plugin icon and the next on the doorhanger thing.

---

