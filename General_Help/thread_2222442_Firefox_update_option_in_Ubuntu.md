---
title: "Firefox update option in Ubuntu"
date: 2014-05-06
forum: General Help
---

### Post by mountainman70 on 2014-05-06
Running Ubuntu 12.04 with Mate on one computer and Ubuntu 14.04 with Mate on a test computer. Both with Firefox 29.
My question is when I go to edit-preferences-advanced-update I only have the option to update search engines. I know it has been like this for some time now. Is there a way to get the options back as they are in W7? These are the options I would like back if it is possible:

Automatically install updates (recommended improved security)
check for updates but let me choose whether to install them
Never check for updates (not recommended security risk)

Or is this just something I must live with in Ubuntu?

---

### Post by monkeybrain20122 on 2014-05-06
In Ubuntu Firefox is updated automatically through the normal software channel,--update manager, synaptic, apt-get etc. Those options are not needed.

---

### Post by mountainman70 on 2014-05-06
> **monkeybrain20122 said:**
> In Ubuntu Firefox is updated automatically through the normal software channel,--update manager, synaptic, apt-get etc. Those options are not needed.

Yes I understand that is how it works. Is there a way to stop auto updates? This update to FF 29 is a good example of waiting a couple of days until all the bugs were worked out.:)

---

### Post by deadflowr on 2014-05-06
> **mountainman70 said:**
> Yes I understand that is how it works. Is there a way to stop auto updates? This update to FF 29 is a good example of waiting a couple of days until all the bugs were worked out.:)

Don't apply them, then.

Unless you have configured unattended-upgrades, you have to actually apply the updates when they come.

Edit: Added, check your software sources > updates to see what the setting are for what to do about security updates.
Normal should be simply "Display".

---

### Post by monkeybrain20122 on 2014-05-06
> **mountainman70 said:**
> Yes I understand that is how it works. Is there a way to stop auto updates? This update to FF 29 is a good example of waiting a couple of days until all the bugs were worked out.:)

Use synaptic to manual update and disable/ignore update manager. If you want to wait a few days then just don't click the box.

The FF update options would not work because Firefox is installed in the system and FF's built in updates don't have permission to change those files. On the other hand if you instead download Firefox from Mozilla and put it in your home (no need to install) those option will work, but I don't see the point of that, the Ubuntu build is nicer anyway. :) (Ubuntu's build menu bar appears in the top panel, vanilla has no menu bar and if manually activate it will show up between the top panel and the tabs, thus taking up more space vertically)

---

### Post by Dennis N on 2014-05-06
> Is there a way to stop auto updates? This update to FF 29 is a good example of waiting a couple of days until all the bugs were worked out.

If you don't want a package to update, lock the package version. In Synaptic Package manager, select the package, then **Package > Lock Version**. You could have done this on FF28, then it would not have upgraded to FF29. Further, it would not remind you that the upgrade is available. When you decide to upgrade, repeat and choose Unlock.

The update options you mention in your post are on the Mozilla Build of Firefox.

---

### Post by mountainman70 on 2014-05-06
Thanks everyone. That explains it for me and anyone else who reads this post. I believe I will lock it in Synaptic package Manager. It's not like I don't see FF updates posted somewhere-sometime.:)
Thanks again.

---

### Post by monkeybrain20122 on 2014-05-06
Locking it is a bad idea because you will want FF to update, just to put it off for a few days. So all you need is not to select it while running update in synaptic.

---

### Post by deadflowr on 2014-05-06
> **monkeybrain20122 said:**
> Locking it is a bad idea because you will want FF to update, just to put it off for a few days. So all you need is not to select it while running update in synaptic.

Or update manager.
You can select or unselect updates in there, too.

---

### Post by mountainman70 on 2014-05-06
Thanks monkeybrain20122 and deadflowr. That is what i will do.

---

