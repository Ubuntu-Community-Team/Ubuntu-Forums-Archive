---
title: "Firefox not recognizing Kaffeine plugin in Kubuntu"
date: 2008-02-05
forum: General Help
---

### Post by beesee on 2008-02-05
After a fresh Kubuntu install I went to install firefox and then kaffeine-mozilla.  However, it's not listed under about:plugins (but Java and Flash are).  Konqueror can see the Kaffeine plugin, but not Firefox.  What's going on?

---

### Post by kuja on 2008-02-05
Its becuase it's not in Firefox's plugin path. You either need to a) find the setting for firefox's plugin path and add this location: /usr/lib/mozilla/plugins/ (good luck with that, I couldn't find it) or b) run this command:

sudo cp /usr/lib/mozilla/plugins/kaffeineplugin.* /usr/lib/firefox/plugins

---

### Post by beesee on 2008-02-06
Bleh, I should've looked there first.  A few links fixed everything, thanks.  But still, shouldn't firefox look for plugins in the mozilla directory by default?  Or I guess another way would be for the kaffeine plugin to look for firefox and make the links automatically.

---

